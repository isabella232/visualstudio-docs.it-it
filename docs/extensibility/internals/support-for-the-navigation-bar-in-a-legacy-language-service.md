---
title: Supporto per la barra di spostamento in un servizio di linguaggio Legacy Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f86dabb0594b1e33c45808efb387fcbe313e3de3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704854"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Supporto per la barra di spostamento in un servizio di linguaggio legacy
La barra di navigazione nella parte superiore della visualizzazione dell'editor visualizza i tipi e i membri nel file. I tipi vengono visualizzati nell'elenco a discesa a sinistra e i membri nell'elenco a discesa a destra. Quando l'utente seleziona un tipo, il accento sbarramento viene posizionato sulla prima riga del tipo. Quando l'utente seleziona un membro, il accento di cuore viene posizionato sulla definizione del membro. Le caselle di riepilogo a discesa vengono aggiornate per riflettere la posizione corrente del punto di inserimento.

## <a name="displaying-and-updating-the-navigation-bar"></a>Visualizzazione e aggiornamento della barra di navigazione
 Per supportare la barra di spostamento, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> è necessario <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> derivare una classe dalla classe e implementare il metodo . Quando al servizio di linguaggio viene <xref:Microsoft.VisualStudio.Package.LanguageService> assegnata una <xref:Microsoft.VisualStudio.Package.CodeWindowManager>finestra del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> codice, la classe base crea un'istanza di , che contiene l'oggetto che rappresenta la finestra del codice. All'oggetto <xref:Microsoft.VisualStudio.Package.CodeWindowManager> viene quindi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> assegnato un nuovo oggetto. Il <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metodo <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> ottiene un oggetto. Se si restituisce <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> un'istanza <xref:Microsoft.VisualStudio.Package.CodeWindowManager> della <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> classe, il metodo chiama <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metodo per popolare gli elenchi interni e passa l'oggetto al gestore della barra a discesa. Il gestore delle barre a discesa, a sua volta, chiama il metodo <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> sull'oggetto per stabilire l'oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> che contiene le due barre a discesa.

 Quando il punto di <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> inserimento <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> si sposta, il metodo chiama il metodo . Il <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> metodo di <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> base <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> chiama il metodo nella classe per aggiornare lo stato della barra di spostamento. Si passa un <xref:Microsoft.VisualStudio.Package.DropDownMember> set di oggetti a questo metodo. Ogni oggetto rappresenta una voce nell'elenco a discesa.

## <a name="the-contents-of-the-navigation-bar"></a>Contenuto della barra di navigazione
 La barra di navigazione contiene in genere un elenco di tipi e un elenco di membri. L'elenco dei tipi include tutti i tipi disponibili nel file di origine corrente. I nomi dei tipi includono le informazioni complete sullo spazio dei nomi. Di seguito è riportato un esempio di codice c'è con due tipi:

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

 Verrà visualizzato `TestLanguagePackage.TestLanguageService` l'elenco dei tipi e `TestLanguagePackage.TestLanguageService.Tokens`.

 Nell'elenco dei membri vengono visualizzati i membri disponibili del tipo selezionato nell'elenco dei tipi. Utilizzando l'esempio di `TestLanguagePackage.TestLanguageService` codice precedente, se è il tipo selezionato, l'elenco dei membri conterrà i membri `tokens` privati e `serviceName`. La struttura `Token` interna non viene visualizzata.

 È possibile implementare l'elenco dei membri per rendere il nome di un membro in grassetto quando il accento testo viene posizionato al suo interno. I membri possono anche essere visualizzati in grigio, a indicare che non si trovano all'interno dell'ambito in cui è attualmente posizionato il punto di inserimento.

## <a name="enabling-support-for-the-navigation-bar"></a>Abilitazione del supporto per la barra di spostamento
 Per abilitare il supporto per la `ShowDropdownBarOption` barra <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> di `true`spostamento, è necessario impostare il parametro dell'attributo su . Questo parametro imposta la proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>. Per supportare la barra di <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> spostamento, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> è <xref:Microsoft.VisualStudio.Package.LanguageService> necessario implementare l'oggetto nel metodo nella classe .

 Nell'implementazione <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> del metodo, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> se la `true`proprietà è <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> impostata su , è possibile restituire un oggetto. Se non si restituisce l'oggetto, la barra di navigazione non viene visualizzata.

 L'opzione per visualizzare la barra di spostamento può essere impostata dall'utente, pertanto è possibile che questo controllo venga reimpostato mentre la visualizzazione dell'editor è aperta. L'utente deve chiudere e riaprire la finestra dell'editor prima che avvenga la modifica.

## <a name="implementing-support-for-the-navigation-bar"></a>Implementazione del supporto per la barra di spostamentoImplementing Support for the Navigation Bar
 Il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo accetta due elenchi (uno per ogni elenco a discesa) e due valori che rappresentano la selezione corrente in ogni elenco. Gli elenchi e i valori di selezione <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> possono essere `true` aggiornati, nel qual caso il metodo deve tornare per indicare che gli elenchi sono stati modificati.

 Quando la selezione cambia nell'elenco a discesa dei tipi, l'elenco dei membri deve essere aggiornato per riflettere il nuovo tipo. Ciò che viene visualizzato nell'elenco dei membri può essere:

- Elenco di membri per il tipo corrente.

- Tutti i membri disponibili nel file di origine, ma con tutti i membri non nel tipo corrente visualizzati in grigio. L'utente può comunque selezionare i membri in grigio, in modo che possano essere utilizzati per la navigazione rapida, ma il colore indica che non fanno parte del tipo attualmente selezionato.

  Un'implementazione <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> del metodo esegue in genere i passaggi seguenti:

1. Ottenere un elenco delle dichiarazioni correnti per il file di origine.

     Esistono diversi modi per popolare gli elenchi. Un approccio consiste nel creare un <xref:Microsoft.VisualStudio.Package.LanguageService> metodo personalizzato <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> nella versione della classe che chiama il metodo con un motivo di analisi personalizzato che restituisce un elenco di tutte le dichiarazioni. Un altro approccio <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> potrebbe essere <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> quello di chiamare il metodo direttamente dal metodo con il motivo di analisi personalizzato. Un terzo approccio potrebbe consistere <xref:Microsoft.VisualStudio.Package.AuthoringScope> nel memorizzare nella cache le dichiarazioni <xref:Microsoft.VisualStudio.Package.LanguageService> nella classe restituita dall'ultima operazione di analisi completa nella classe e recuperarla dal <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo.

2. Popolare o aggiornare l'elenco dei tipi.

     Il contenuto dell'elenco dei tipi può essere aggiornato quando l'origine è stata modificata o se si è scelto di modificare lo stile del testo dei tipi in base alla posizione corrente del testo. Si noti che questa <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> posizione viene passata al metodo.

3. Determinare il tipo da selezionare nell'elenco dei tipi in base alla posizione corrente del cuore di inserimento.

     È possibile cercare le dichiarazioni ottenute nel passaggio 1 per trovare il tipo che racchiude la posizione del punto di inserimento corrente e quindi cercare nell'elenco dei tipi il tipo per determinarne l'indice nell'elenco dei tipi.

4. Popolare o aggiornare l'elenco dei membri in base al tipo selezionato.

     L'elenco dei membri riflette ciò che è attualmente visualizzato nell'elenco a discesa **Membri.** Potrebbe essere necessario aggiornare il contenuto dell'elenco dei membri se l'origine è stata modificata o se si visualizzano solo i membri del tipo selezionato e il tipo selezionato. Se si sceglie di visualizzare tutti i membri nel file di origine, lo stile del testo di ogni membro nell'elenco deve essere aggiornato se il tipo attualmente selezionato è stato modificato.

5. Determinare il membro da selezionare nell'elenco dei membri in base alla posizione corrente del cuore di inserimento.

     Cercare nelle dichiarazioni ottenute nel passaggio 1 il membro che contiene la posizione corrente del punto di inserimento, quindi cercare tale membro nell'elenco dei membri per determinarne l'indice nell'elenco dei membri.

6. Restituire `true` se sono state apportate modifiche agli elenchi o alle selezioni in entrambi gli elenchi.
