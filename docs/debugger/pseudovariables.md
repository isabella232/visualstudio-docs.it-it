---
title: Le pseudo variabili | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbfd275625e949e87e2b4109e1d56eaeaf9d7e3c
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2019
ms.locfileid: "59366848"
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Pseudo variabili nel debugger di Visual Studio
Le pseudo variabili sono termini usati per visualizzare determinate informazioni in una finestra delle variabili o nella finestra di dialogo **Controllo immediato**. È possibile immettere una pseudo variabile in modo analogo all'immissione di una variabile normale. Tuttavia, le pseudo variabili non sono variabili e non corrispondono a nomi di variabili presenti nel programma.

## <a name="example"></a>Esempio
 Si supponga di scrivere un'applicazione in codice nativo e di voler visualizzare il numero di handle allocati nell'applicazione. Nella finestra **Espressioni di controllo**, è possibile immettere la seguente pseudo variabile nella colonna **Nome**, quindi premere Invio per valutarla:

`$handles`

 Nel codice nativo, è possibile usare le pseudo variabili riportate nella tabella seguente:

|Pseudo variabile|Funzione|
|--------------------|--------------|
|`$err`|Visualizza l'ultimo set di valori di errore con la funzione SetLastError. Il valore visualizzato rappresenta ciò che viene restituito dalla funzione GetLastError.<br /><br /> Usare `$err,hr` per vedere il formato decodificato di questo valore. Ad esempio, se l'ultimo errore era 3, `$err,hr` visualizza `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|
|`$handles`|Consente di visualizzare il numero di handle allocati nell'applicazione.|
|`$vframe`|Consente di visualizzare l'indirizzo dello stack frame corrente.|
|`$tid`|Consente di visualizzare l'ID del thread corrente.|
|`$env`|Visualizza il blocco di ambiente nel visualizzatore stringhe.|
|`$cmdline`|Visualizza la stringa della riga di comando che ha avviato il programma.|
|`$pid`|Visualizza l'ID del processo.|
|`$` *registername*<br /><br /> oppure<br /><br /> `@` *registername*|Visualizza i contenuti del registro *registername*.<br /><br /> In genere, è possibile visualizzare il contenuto del registro immettendone semplicemente il nome. È necessario usare questa sintassi unicamente quando il nome del registro esegue l'overload di un nome di variabile. Se il nome del registro è uguale a un nome di variabile nell'ambito corrente, il debugger lo interpreta come nome di variabile. In questo caso, è opportuno usare `$`*registername* o `@`*registername*.|
|`$clk`|Consente di visualizzare il tempo in cicli di orologio.|
|`$user`|Consente di visualizzare una struttura con le informazioni sull'account in cui viene eseguita l'applicazione. Per motivi di sicurezza non vengono visualizzate informazioni sulla password.|
|`$exceptionstack`|Visualizza la traccia dello stack dell'eccezione corrente di Windows Runtime. `$ exceptionstack` funziona solo nelle App UWP. `$ exceptionstack` non è supportata per le eccezioni C++ e SEH|
|`$returnvalue`|Visualizza il valore restituito di un metodo .NET Framework.|

 In C# è possibile usare le pseudo variabili riportate nella tabella seguente:

|Pseudo variabile|Funzione|
|--------------------|--------------|
|`$exception`|Visualizza informazioni sull'ultima eccezione. Se non si è verificata alcuna eccezione, la valutazione di `$exception` produce un messaggio di errore.<br /><br /> Quando le informazioni sulle eccezioni è disabilitata, `$exception` viene automaticamente aggiunto per il **variabili locali** finestra quando viene generata un'eccezione.|
|`$user`|Consente di visualizzare una struttura con le informazioni sull'account in cui viene eseguita l'applicazione. Per motivi di sicurezza non vengono visualizzate informazioni sulla password.|
|`$returnvalue`|Visualizza il valore restituito di un metodo .NET Framework.|

 In Visual Basic, è possibile usare le pseudo variabili riportate nella tabella seguente:

|Pseudo variabile|Funzione|
|--------------------|--------------|
|`$exception`|Visualizza informazioni sull'ultima eccezione. Se non si è verificata alcuna eccezione, la valutazione di `$exception` produce un messaggio di errore.|
|`$delete` o `$$delete`|Elimina una variabile implicita creata nella finestra **Immediata**. La sintassi è `$delete,` *variabile* oppure`$delete,` *variabile*`.`|
|`$objectids` o `$listobjectids`|Visualizza tutti gli ID oggetto attivi come figli dell'espressione specificata. La sintassi è `$objectid,` *espressione* oppure`$listobjectids,` *espressione*`.`|
|`$` *N* `#`|Visualizza l'oggetto con ID dell'oggetto uguale a *N*.|
|`$dynamic`|Visualizza il nodo **Visualizzazione dinamica** speciale per un oggetto che implementa `IDynamicMetaObjectProvider`. Interfaccia. La sintassi è `$dynamic,` *object*. Questa funzionalità si applica solo al codice che usa .NET Framework versione 4.|

## <a name="see-also"></a>Vedere anche
- [Finestre Espressioni di controllo e Controllo immediato](../debugger/watch-and-quickwatch-windows.md)
- [Finestra delle variabili](../debugger/debugger-windows.md)
