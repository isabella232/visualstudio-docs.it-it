---
title: Refactoring (C#) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0415222645dce2f65e91b5b1c55a5a118cc26697
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667507"
---
# <a name="refactoring-c"></a>Refactoring (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il refactoring è il processo di miglioramento del codice dopo che è stato scritto modificando la struttura interna del codice senza modificare il comportamento esterno del codice.

 Visual C# fornisce i comandi di refactoring seguenti nel menu **refactoring** :

- [Refactoring per Estrai Metodo (C#)](../csharp-ide/extract-method-refactoring-csharp.md)

- [Refactoring per Rinomina (C#)](../csharp-ide/rename-refactoring-csharp.md)

- [Refactoring per Incapsula campo (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)

- [Refactoring per Estrai interfaccia (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)

- [Refactoring per Rimuovi parametri (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)

- [Refactoring per Riordina parametri (C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)

## <a name="multi-project-refactoring"></a>Refactoring di più progetti
 Visual Studio supporta il Refactoring multiprogetto per i progetti che si trovano nella stessa soluzione. Tutte le operazioni di refactoring che correggono i riferimenti tra i file correggono i riferimenti in tutti i progetti della stessa lingua. Funziona per qualsiasi riferimento da progetto a progetto. Se, ad esempio, si dispone di un'applicazione console che fa riferimento a una libreria di classi, quando si rinomina un tipo di libreria di classi (usando l' `Rename` operazione di refactoring), vengono aggiornati anche i riferimenti al tipo di libreria di classi nell'applicazione console.

## <a name="changes-preview"></a>Anteprima modifiche
 Molte operazioni di refactoring consentono di esaminare tutte le modifiche di riferimento eseguite da un'operazione di refactoring sul codice, prima di eseguire il commit delle modifiche. Per queste operazioni di refactoring, nella finestra di dialogo refactoring verrà visualizzata un'opzione **Anteprima modifiche riferimenti** . Dopo aver selezionato l'opzione e accettato l'operazione di refactoring, verrà visualizzata la finestra di **dialogo Anteprima modifiche** . Si noti che nella finestra di dialogo **Anteprima modifiche** sono presenti due visualizzazioni. Nella visualizzazione inferiore viene visualizzato il codice con tutti gli aggiornamenti di riferimento a causa dell'operazione di refactoring. Se si preme **Annulla** nella finestra di dialogo **Anteprima modifiche** , l'operazione di refactoring verrà arrestata e non verrà apportata alcuna modifica al codice.

## <a name="refactoring-warnings"></a>Refactoring degli avvisi
 Se il compilatore non ha una conoscenza completa del programma ed è possibile che il motore di refactoring non aggiorni tutti i riferimenti appropriati, viene visualizzata la finestra di dialogo di avviso. Questa finestra di dialogo di avviso consente inoltre di visualizzare l'anteprima del codice nella finestra di dialogo **Anteprima modifiche** prima di eseguire il commit delle modifiche.

> [!NOTE]
> Se un metodo contiene un errore di sintassi (che l'IDE indica con una sottolineatura ondulata rossa), il motore di refactoring non aggiornerà alcun riferimento a un elemento all'interno di tale metodo. Nell'esempio seguente viene illustrato questo comportamento.

 Per impostazione predefinita, se si esegue un'operazione di refactoring senza visualizzare in anteprima le modifiche al riferimento e viene rilevato un errore di compilazione nel programma, l'ambiente di sviluppo Visualizza questa finestra di dialogo di avviso.

 Se si esegue un'operazione di refactoring con le **modifiche al riferimento in anteprima** abilitate e viene rilevato un errore di compilazione nel programma, nell'ambiente di sviluppo verrà visualizzato il seguente messaggio di avviso nella parte inferiore della finestra di dialogo **Anteprima modifiche** , invece di visualizzare la finestra di dialogo di **avviso di refactoring** :

 **Il progetto o una delle relative dipendenze non è attualmente in fase di compilazione. Non è possibile aggiornare i riferimenti.**

 Questo avviso di refactoring è disponibile solo per le operazioni di refactoring che forniscono l'opzione **Anteprima modifiche riferimenti** .

## <a name="error-tolerant-refactoring-and-verification-results"></a>Refactoring e risultati della verifica a tolleranza di errore
 Il refactoring è a tolleranza di errore. In altre parole, è possibile eseguire un refactoring in un progetto che non può essere compilato. In questi casi, tuttavia, il processo di refactoring potrebbe non aggiornare correttamente i riferimenti ambigui.

 La finestra di dialogo **Risultati verifica** consente di ricevere una notifica se il motore di refactoring rileva errori di compilazione o rileva che un'operazione di refactoring causa inavvertitamente un riferimento al codice associato a un elemento diverso da quello in cui è stato originariamente associato (problema di riassociazione).

 Per attivare la funzionalità risultati di verifica, scegliere **Opzioni**dal menu **strumenti** . Nella finestra di dialogo **Opzioni** espandere **editor di testo**, quindi espandere **C#**. Fare clic su **Avanzate** e selezionare la casella **di controllo Verifica risultati della refactoring** .

 La finestra di dialogo **Risultati verifica** distingue la differenza tra due tipi di problemi di riassociazione.

### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>Riferimenti la cui definizione non sarà più il simbolo rinominato
 Questo tipo di problema di riassociazione si verifica quando un riferimento non fa più riferimento a un simbolo rinominato. Si consideri il codice di esempio seguente:

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

 Se si usa il refactoring per rinominare `a` in `b` , viene visualizzata questa finestra di dialogo. Il riferimento alla variabile rinominata `a` ora viene associato al parametro passato al costruttore anziché all'associazione al campo.

### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Riferimenti la cui definizione diventerà ora il simbolo rinominato
 Questo tipo di problema di riassociazione si verifica quando un riferimento che in precedenza non faceva riferimento al simbolo rinominato ora fa riferimento al simbolo rinominato. Si consideri il codice di esempio seguente:

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

 Se si usa il refactoring per rinominare `OtherMethod` in `Method` , viene visualizzata questa finestra di dialogo. Il riferimento in `Main` ora fa riferimento al metodo di overload che accetta un `int` parametro anziché il metodo di overload che accetta un `object` parametro.

## <a name="see-also"></a>Vedere anche
 [Uso dell'ambiente di sviluppo di Visual Studio per C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) [procedura: ripristinare i frammenti di codice di refactoring di c#](../ide/how-to-restore-csharp-refactoring-snippets.md)