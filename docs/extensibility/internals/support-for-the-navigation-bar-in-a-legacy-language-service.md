---
title: Supportare la barra di spostamento in un servizio di linguaggio legacy
description: Informazioni su come supportare la barra di spostamento in un servizio di linguaggio legacy. La barra di spostamento nella visualizzazione dell'editor visualizza i tipi e i membri nel file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 497fd019b0da6beac7776af6926aa24d677813f3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069637"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Supporto per la barra di spostamento in un servizio di linguaggio legacy
Nella barra di spostamento nella parte superiore della visualizzazione dell'editor vengono visualizzati i tipi e i membri nel file. I tipi vengono visualizzati nell'elenco a discesa a sinistra e i membri vengono visualizzati nell'elenco a discesa a destra. Quando l'utente seleziona un tipo, il punto di interruzione viene inserito nella prima riga del tipo. Quando l'utente seleziona un membro, il punto di selezione viene inserito nella definizione del membro. Le caselle a discesa vengono aggiornate per riflettere la posizione corrente del punto di selezione.

## <a name="displaying-and-updating-the-navigation-bar"></a>Visualizzazione e aggiornamento della barra di spostamento
 Per supportare la barra di spostamento, è necessario derivare una classe dalla <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> classe e implementare il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo . Quando al servizio di linguaggio viene data una finestra del codice, la classe base crea un'istanza di , che contiene l'oggetto <xref:Microsoft.VisualStudio.Package.LanguageService> che rappresenta la finestra del <xref:Microsoft.VisualStudio.Package.CodeWindowManager> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> codice. <xref:Microsoft.VisualStudio.Package.CodeWindowManager>All'oggetto viene quindi assegnato un nuovo oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . Il <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metodo ottiene un oggetto <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> . Se si restituisce un'istanza della classe , chiama il metodo per popolare gli elenchi interni e passa l'oggetto al gestore <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> <xref:Microsoft.VisualStudio.Package.CodeWindowManager> della barra a <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] discesa. Il gestore della barra a discesa, a sua volta, chiama il metodo sull'oggetto per stabilire l'oggetto che contiene le <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> due barre a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> discesa.

 Quando il cursore viene spostato, <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> il metodo chiama il metodo <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> . Il metodo di base <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> chiama il metodo nella classe per aggiornare lo stato della barra di <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> spostamento. Si passa un set di <xref:Microsoft.VisualStudio.Package.DropDownMember> oggetti a questo metodo. Ogni oggetto rappresenta una voce nell'elenco a discesa.

## <a name="the-contents-of-the-navigation-bar"></a>Contenuto della barra di spostamento
 La barra di spostamento contiene in genere un elenco di tipi e un elenco di membri. L'elenco dei tipi include tutti i tipi disponibili nel file di origine corrente. I nomi dei tipi includono le informazioni complete sullo spazio dei nomi. Di seguito è riportato un esempio di codice C# con due tipi:

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

 Nell'elenco dei tipi verranno visualizzati `TestLanguagePackage.TestLanguageService` e `TestLanguagePackage.TestLanguageService.Tokens` .

 Nell'elenco dei membri vengono visualizzati i membri disponibili del tipo selezionato nell'elenco dei tipi. Usando l'esempio di codice precedente, se è il tipo selezionato, l'elenco dei membri conterrà `TestLanguagePackage.TestLanguageService` i membri privati e `tokens` `serviceName` . La struttura interna `Token` non viene visualizzata.

 È possibile implementare l'elenco di membri per rendere il nome di un membro in grassetto quando il punto di selezione viene inserito al suo interno. I membri possono anche essere visualizzati in grigio, a indicare che non sono all'interno dell'ambito in cui è attualmente posizionato il cursore.

## <a name="enabling-support-for-the-navigation-bar"></a>Abilitazione del supporto per la barra di spostamento
 Per abilitare il supporto per la barra di spostamento, è necessario impostare il `ShowDropdownBarOption` parametro <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> dell'attributo su `true` . Questo parametro imposta la proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>. Per supportare la barra di spostamento, è necessario <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> implementare l'oggetto nel <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe .

 Nell'implementazione del <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metodo , se la proprietà è <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> impostata su , è possibile restituire `true` un oggetto <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> . Se non si restituisce l'oggetto , la barra di spostamento non viene visualizzata.

 L'opzione per visualizzare la barra di spostamento può essere impostata dall'utente, pertanto è possibile reimpostare questo controllo mentre la visualizzazione dell'editor è aperta. L'utente deve chiudere e riaprire la finestra dell'editor prima che venga apportata la modifica.

## <a name="implementing-support-for-the-navigation-bar"></a>Implementazione del supporto per la barra di spostamento
 Il metodo accetta due elenchi (uno per ogni elenco a discesa) e due valori che <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> rappresentano la selezione corrente in ogni elenco. Gli elenchi e i valori di selezione possono essere aggiornati, nel qual caso il metodo deve restituire per <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> indicare che gli elenchi sono stati `true` modificati.

 Quando la selezione cambia nell'elenco a discesa dei tipi, l'elenco dei membri deve essere aggiornato per riflettere il nuovo tipo. Gli elementi visualizzati nell'elenco dei membri possono essere:

- Elenco di membri per il tipo corrente.

- Tutti i membri disponibili nel file di origine, ma con tutti i membri non del tipo corrente visualizzati in grigio. L'utente può comunque selezionare i membri disattivati, in modo che possano essere usati per la navigazione rapida, ma il colore indica che non fanno parte del tipo attualmente selezionato.

  Un'implementazione <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> del metodo esegue in genere la procedura seguente:

1. Ottiene un elenco di dichiarazioni correnti per il file di origine.

     Esistono diversi modi per popolare gli elenchi. Un approccio consiste nel creare un metodo personalizzato nella versione della classe che chiama il metodo con un motivo di analisi personalizzato che restituisce un elenco <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> di tutte le dichiarazioni. Un altro approccio potrebbe consistere nel chiamare <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> il metodo direttamente dal metodo con il motivo di analisi <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> personalizzato. Un terzo approccio potrebbe consistere nel memorizzare nella cache le dichiarazioni nella classe restituita dall'ultima operazione di analisi completa nella classe e recuperata <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.LanguageService> dal metodo <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> .

2. Popolare o aggiornare l'elenco di tipi.

     Il contenuto dell'elenco dei tipi può essere aggiornato quando l'origine è stata modificata o se si è scelto di modificare lo stile del testo dei tipi in base alla posizione del cursore corrente. Si noti che questa posizione viene passata al <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo .

3. Determinare il tipo da selezionare nell'elenco dei tipi in base alla posizione corrente del cursore.

     È possibile cercare le dichiarazioni ottenute nel passaggio 1 per trovare il tipo che racchiude la posizione del cursore corrente e quindi cercare tale tipo nell'elenco dei tipi per determinarne l'indice nell'elenco dei tipi.

4. Popolare o aggiornare l'elenco di membri in base al tipo selezionato.

     L'elenco dei membri riflette ciò che è attualmente visualizzato **nell'elenco a** discesa Membri. Potrebbe essere necessario aggiornare il contenuto dell'elenco di membri se l'origine è stata modificata o se vengono visualizzati solo i membri del tipo selezionato e il tipo selezionato è stato modificato. Se si sceglie di visualizzare tutti i membri nel file di origine, lo stile del testo di ogni membro nell'elenco deve essere aggiornato se il tipo attualmente selezionato è stato modificato.

5. Determinare il membro da selezionare nell'elenco dei membri in base alla posizione corrente del cursore.

     Cercare nelle dichiarazioni ottenute nel passaggio 1 il membro che contiene la posizione del cursore corrente, quindi cercare tale membro nell'elenco dei membri per determinarne l'indice nell'elenco dei membri.

6. Restituisce `true` se sono state apportate modifiche agli elenchi o alle selezioni in uno degli elenchi.
