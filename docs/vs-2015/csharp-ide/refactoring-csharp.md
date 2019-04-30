---
title: Refactoring (c#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.csharp.refactoring.preview
- vs.csharp.refactoring.issues
- vs.csharp.refactoring.buildwarning
- VS.PreviewChanges
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#]
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fa8fbfd8837fb35617b79089fffd11ea3b8d2e93
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444537"
---
# <a name="refactoring-c"></a>Refactoring (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Refactoring è il processo di miglioramento del codice dopo che è stata scritta modificando la struttura interna del codice senza modificare il comportamento esterno del codice.  
  
 Visual c# fornisce i seguenti comandi di refactoring nel **Refactoring** menu:  
  
- [Refactoring per Estrai Metodo (C#)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
- [Refactoring per Rinomina (C#)](../csharp-ide/rename-refactoring-csharp.md)  
  
- [Refactoring per Incapsula campo (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
- [Refactoring per Estrai interfaccia (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
- [Refactoring per Rimuovi parametri (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
- [Refactoring per Riordina parametri (C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## <a name="multi-project-refactoring"></a>Refactoring con più progetti  
 Visual Studio supporta il refactoring di più progetti per i progetti che sono nella stessa soluzione. Tutte le operazioni di refactoring che correggere i riferimenti tra file correggere tali riferimenti a tutti i progetti della stessa lingua. Questa opzione funziona per tutti i riferimenti da progetto a progetto. Ad esempio, se si dispone di un'applicazione console che fa riferimento a una libreria di classi, quando si rinomina un tipo di libreria di classi (usando il `Rename` operazione di refactoring), vengono aggiornati anche i riferimenti al tipo di libreria di classi nell'applicazione console.  
  
## <a name="changes-preview"></a>Anteprima modifiche  
 Molte operazioni di refactoring forniscono un'opportunità esaminare tutte le modifiche di riferimento che un'operazione di refactoring verrà eseguite nel codice, prima di eseguire il commit delle modifiche. Per queste operazioni, di refactoring una **Anteprima modifiche riferimento** refactoring nella finestra di dialogo viene visualizzata l'opzione. Dopo aver selezionato questa opzione e accettare l'operazione di refactoring, il **finestra di dialogo Anteprima modifiche** verranno visualizzati. Si noti che il **Anteprima modifiche** nella finestra di dialogo è disponibili due visualizzazioni. La parte inferiore verranno visualizzati il codice con tutti gli aggiornamenti di riferimento a causa dell'operazione di refactoring. Premendo **annullare** nel **Anteprima modifiche** nella finestra di dialogo interromperà l'operazione di refactoring, e non sarà possibile apportare modifiche al codice.  
  
## <a name="refactoring-warnings"></a>Avvisi di refactoring  
 Il compilatore non ha una conoscenza completa del programma, se è possibile che il motore di refactoring non aggiorni tutti i riferimenti appropriati, viene visualizzata la finestra di dialogo di avviso. Questa finestra di dialogo di avviso fornisce anche un'opportunità visualizzare l'anteprima del codice nel **Anteprima modifiche** finestra di dialogo prima del commit delle modifiche.  
  
> [!NOTE]
> Se un metodo contiene un errore di sintassi (indicante l'IDE con una sottolineatura ondulata rossa), il motore di refactoring non aggiornerà tutti i riferimenti a un elemento all'interno di tale metodo. L'esempio seguente illustra questo comportamento.  
  
 Per impostazione predefinita, se si esegue un'operazione di refactoring senza visualizzare l'anteprima di riferimento viene modificato e viene rilevato un errore di compilazione nel programma, quindi l'ambiente di sviluppo consente di visualizzare la finestra di dialogo.  
  
 Se si esegue un'operazione di refactoring dotato **Anteprima modifiche riferimento** abilitato e viene rilevato un errore di compilazione nel programma, quindi l'ambiente di sviluppo verrà visualizzato il seguente messaggio di avviso nella parte inferiore del **Anteprima modifiche** della finestra di dialogo anziché la finestra di **Refactoring avviso** nella finestra di dialogo:  
  
 **Compilare il progetto o una delle relative dipendenze non attualmente. I riferimenti potrebbero non essere aggiornati.**  
  
 Questo avviso di refactoring è disponibile solo per operazioni di refactoring che forniscono i **Anteprima modifiche riferimento** opzione.  
  
## <a name="error-tolerant-refactoring-and-verification-results"></a>Refactoring con tolleranza di errore e risultati della verifica  
 Il refactoring è a tolleranza di errore. In altre parole, è possibile eseguire un'operazione di refactoring in un progetto che non è possibile compilare. Tuttavia, in questi casi il processo di refactoring non aggiorni riferimenti ambigui correttamente.  
  
 Il **risultati della verifica** nella finestra di dialogo può ricevere una notifica se il motore di refactoring rilevi errori di compilazione o che un'operazione di refactoring provoca inavvertitamente un riferimento al codice per l'associazione a un elemento diverso da quello associato in origine (riassociazione problema).  
  
 Per attivare la funzionalità dei risultati della verifica, scegliere il **strumenti** menu, fare clic su **opzioni**. Nel **le opzioni** finestra di dialogo espandere **Editor di testo**, quindi espandere **c#**. Fare clic su **avanzate** e selezionare il **verifica risultati del refactoring** casella di controllo.  
  
 Il **risultati della verifica** nella finestra di dialogo consente di distinguere la differenza tra due tipi di problemi di riassociazione.  
  
### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>Riferimenti a cui la definizione non sarà più possibile il simbolo rinominato  
 Questo tipo di problema riassociazione si verifica quando un riferimento non fa più riferimento a un simbolo rinominato. Si consideri il codice di esempio seguente:  
  
```csharp  
class Example  
{  
    private int a;  
    public Example(int b)  
    {  
        a = b;  
    }  
}  
```  
  
 Se si usa il refactoring per rinominare `a` a `b`, viene visualizzata questa finestra di dialogo. Il riferimento alla variabile rinominata `a` ora associato al parametro passato al costruttore anziché l'associazione al campo.  
  
### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Riferimenti la cui definizione diventerà il simbolo rinominato  
 Questo tipo di problema riassociazione si verifica quando un riferimento che in precedenza non fa riferimento al simbolo rinominato ora fare riferimento ai simboli rinominati. Si consideri il codice di esempio seguente:  
  
```csharp  
class Example  
{  
    private static void Method(object a) { }  
    private static void OtherMethod(int a) { }  
    static void Main(string[] args)  
    {  
        Method(5);  
    }  
}  
```  
  
 Se si usa il refactoring per rinominare `OtherMethod` a `Method`, viene visualizzata questa finestra di dialogo. Il riferimento nel `Main` fa riferimento al metodo di overload che accetta un `int` parametro anziché il metodo di overload che accetta un `object` parametro.  
  
## <a name="see-also"></a>Vedere anche  
 [Usando l'ambiente di sviluppo di Visual Studio per c#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [Procedura: Ripristinare refactoring di frammenti C#](../ide/how-to-restore-csharp-refactoring-snippets.md)