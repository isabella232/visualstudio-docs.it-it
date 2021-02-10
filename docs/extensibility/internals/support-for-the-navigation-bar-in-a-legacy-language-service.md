---
title: Supporto della barra di spostamento in un servizio di linguaggio legacy
description: Informazioni su come supportare la barra di spostamento in un servizio di linguaggio legacy. La barra di spostamento nella visualizzazione dell'editor consente di visualizzare i tipi e i membri del file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d33b8452f727037226a50abe6a9493ce132e9564
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932579"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Supporto per la barra di spostamento in un servizio di linguaggio legacy
La barra di navigazione nella parte superiore della visualizzazione dell'editor consente di visualizzare i tipi e i membri del file. I tipi vengono visualizzati nell'elenco a discesa a sinistra e i membri vengono visualizzati nell'elenco a discesa a destra. Quando l'utente seleziona un tipo, il punto di inserimento viene inserito nella prima riga del tipo. Quando l'utente seleziona un membro, il punto di inserimento viene inserito nella definizione del membro. Le caselle di riepilogo a discesa vengono aggiornate in modo da riflettere la posizione corrente del punto di inserimento.

## <a name="displaying-and-updating-the-navigation-bar"></a>Visualizzazione e aggiornamento della barra di spostamento
 Per supportare la barra di navigazione, è necessario derivare una classe dalla <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> classe e implementare il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo. Quando al servizio di linguaggio viene assegnata una finestra del codice, la <xref:Microsoft.VisualStudio.Package.LanguageService> classe base crea un'istanza di <xref:Microsoft.VisualStudio.Package.CodeWindowManager> , che contiene l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> oggetto che rappresenta la finestra del codice. All' <xref:Microsoft.VisualStudio.Package.CodeWindowManager> oggetto viene quindi assegnato un nuovo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto. Il <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metodo ottiene un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> oggetto. Se si restituisce un'istanza della <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> classe, chiama il <xref:Microsoft.VisualStudio.Package.CodeWindowManager> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo per popolare gli elenchi interni e passa l' <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> oggetto alla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestione della barra a discesa. Il gestore della barra a discesa chiama a sua volta il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> metodo sull' <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> oggetto per stabilire l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> oggetto che include le due barre a discesa.

 Quando il punto di inserimento viene spostato, il <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> metodo chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> metodo. Il metodo di base <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> chiama il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo nella <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> classe per aggiornare lo stato della barra di navigazione. Viene passato un set di <xref:Microsoft.VisualStudio.Package.DropDownMember> oggetti a questo metodo. Ogni oggetto rappresenta una voce nell'elenco a discesa.

## <a name="the-contents-of-the-navigation-bar"></a>Contenuto della barra di spostamento
 La barra di spostamento contiene in genere un elenco di tipi e un elenco di membri. L'elenco di tipi include tutti i tipi disponibili nel file di origine corrente. I nomi di tipo includono le informazioni complete sullo spazio dei nomi. Di seguito è riportato un esempio di codice C# con due tipi:

```csharp
namespace TestLanguagePackage
{
    public class TestLanguageService
    {
        internal struct Token
        {
            int tokenID;
        }
        private Tokens[] tokens;
        private string serviceName;
    }
}
```

 Nell'elenco tipo vengono visualizzati `TestLanguagePackage.TestLanguageService` e `TestLanguagePackage.TestLanguageService.Tokens` .

 Nell'elenco dei membri vengono visualizzati i membri disponibili del tipo selezionato nell'elenco tipi. Utilizzando l'esempio di codice precedente, se `TestLanguagePackage.TestLanguageService` è il tipo selezionato, l'elenco dei membri conterrà i membri privati `tokens` e `serviceName` . La struttura interna `Token` non viene visualizzata.

 È possibile implementare l'elenco dei membri per rendere il nome di un membro in grassetto quando il punto di inserimento viene inserito al suo interno. I membri possono anche essere visualizzati in testo in grigio, a indicare che non si trovano all'interno dell'ambito in cui è attualmente posizionato il cursore.

## <a name="enabling-support-for-the-navigation-bar"></a>Abilitazione del supporto per la barra di spostamento
 Per abilitare il supporto per la barra di navigazione, è necessario impostare il `ShowDropdownBarOption` parametro dell' <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo su `true` . Questo parametro imposta la proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>. Per supportare la barra di navigazione, è necessario implementare l' <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> oggetto nel <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metodo della <xref:Microsoft.VisualStudio.Package.LanguageService> classe.

 Nell'implementazione del <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metodo, se la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> proprietà è impostata su `true` , è possibile restituire un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> oggetto. Se non si restituisce l'oggetto, la barra di spostamento non viene visualizzata.

 L'opzione per visualizzare la barra di spostamento può essere impostata dall'utente, pertanto è possibile che il controllo venga reimpostato mentre è aperta la visualizzazione dell'editor. L'utente deve chiudere e riaprire la finestra dell'editor prima che la modifica avvenga.

## <a name="implementing-support-for-the-navigation-bar"></a>Implementazione del supporto per la barra di spostamento
 Il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo accetta due elenchi (uno per ogni elenco a discesa) e due valori che rappresentano la selezione corrente in ogni elenco. Gli elenchi e i valori di selezione possono essere aggiornati, nel qual caso il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo deve restituire `true` per indicare che gli elenchi sono stati modificati.

 Quando si modifica la selezione nell'elenco a discesa tipi, è necessario aggiornare l'elenco dei membri in modo da riflettere il nuovo tipo. Gli elementi visualizzati nell'elenco dei membri possono essere i seguenti:

- Elenco di membri per il tipo corrente.

- Tutti i membri disponibili nel file di origine, ma con tutti i membri non appartenenti al tipo corrente visualizzato in testo in grigio. L'utente può comunque selezionare i membri in grigio, in modo che possano essere usati per la navigazione rapida, ma il colore indica che non fanno parte del tipo attualmente selezionato.

  Un'implementazione del <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo in genere esegue i passaggi seguenti:

1. Ottiene un elenco di dichiarazioni correnti per il file di origine.

     Sono disponibili diversi modi per popolare gli elenchi. Un approccio consiste nel creare un metodo personalizzato sulla versione della <xref:Microsoft.VisualStudio.Package.LanguageService> classe che chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo con un motivo di analisi personalizzato che restituisce un elenco di tutte le dichiarazioni. Un altro approccio potrebbe consistere nel chiamare il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo direttamente dal <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo con il motivo dell'analisi personalizzata. Un terzo approccio potrebbe essere quello di memorizzare nella cache le dichiarazioni della <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe restituite dall'ultima operazione di analisi completa nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe e di recuperarle dal <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo.

2. Popolare o aggiornare l'elenco di tipi.

     Il contenuto dell'elenco dei tipi può essere aggiornato quando l'origine è stata modificata o se si è scelto di modificare lo stile del testo dei tipi in base alla posizione corrente del punto di inserimento. Si noti che questa posizione viene passata al <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo.

3. Determinare il tipo da selezionare nell'elenco dei tipi in base alla posizione corrente del cursore.

     È possibile eseguire una ricerca nelle dichiarazioni ottenute nel passaggio 1 per trovare il tipo che racchiude la posizione corrente del cursore, quindi eseguire una ricerca nell'elenco dei tipi per quel tipo per determinare l'indice nell'elenco dei tipi.

4. Compila o aggiorna l'elenco dei membri in base al tipo selezionato.

     L'elenco dei membri riflette gli elementi attualmente visualizzati nell'elenco a discesa **membri** . Potrebbe essere necessario aggiornare il contenuto dell'elenco di membri se l'origine è stata modificata o se vengono visualizzati solo i membri del tipo selezionato e il tipo selezionato è stato modificato. Se si sceglie di visualizzare tutti i membri nel file di origine, è necessario aggiornare lo stile del testo di ogni membro nell'elenco se il tipo attualmente selezionato è stato modificato.

5. Determinare il membro da selezionare nell'elenco dei membri in base alla posizione corrente del cursore.

     Eseguire una ricerca nelle dichiarazioni ottenute nel passaggio 1 per il membro che contiene la posizione corrente del punto di inserimento, quindi cercare nell'elenco dei membri il membro per determinarne l'indice nell'elenco dei membri.

6. Restituisce `true` se sono state apportate modifiche agli elenchi o alle selezioni in uno degli elenchi.
