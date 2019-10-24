---
title: Pseudo variabili riportate | Microsoft Docs
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
ms.openlocfilehash: e328e85f58e69ef1d579fd979f629c59b90caf3e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730522"
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Pseudo variabili riportate nel debugger di Visual Studio
Le pseudo variabili sono termini usati per visualizzare determinate informazioni in una finestra delle variabili o nella finestra di dialogo **Controllo immediato**. È possibile immettere una pseudo variabile in modo analogo all'immissione di una variabile normale. Tuttavia, le pseudo variabili non sono variabili e non corrispondono a nomi di variabili presenti nel programma.

## <a name="example"></a>Esempio
 Si supponga di scrivere un'applicazione in codice nativo e di voler visualizzare il numero di handle allocati nell'applicazione. Nella finestra **Espressioni di controllo**, è possibile immettere la seguente pseudo variabile nella colonna **Nome**, quindi premere Invio per valutarla:

`$handles`

 Nel codice nativo, è possibile usare il pseudo variabili riportate illustrato nella tabella seguente:

|Pseudo variabile|Funzione|
|--------------------|--------------|
|`$err`|Visualizza l'ultimo set di valori di errore con la funzione SetLastError. Il valore visualizzato rappresenta ciò che viene restituito dalla funzione GetLastError.<br /><br /> Usare `$err,hr` per vedere il formato decodificato di questo valore. Ad esempio, se l'ultimo errore era 3, `$err,hr` visualizza `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|
|`$handles`|Consente di visualizzare il numero di handle allocati nell'applicazione.|
|`$vframe`|Consente di visualizzare l'indirizzo dello stack frame corrente.|
|`$tid`|Consente di visualizzare l'ID del thread corrente.|
|`$env`|Visualizza il blocco di ambiente nel visualizzatore stringhe.|
|`$cmdline`|Visualizza la stringa della riga di comando che ha avviato il programma.|
|`$pid`|Visualizza l'ID del processo.|
|`$` *registername*<br /><br /> Oppure<br /><br /> `@` *registername*|Visualizza i contenuti del registro *registername*.<br /><br /> In genere, è possibile visualizzare il contenuto del registro immettendone semplicemente il nome. È necessario usare questa sintassi unicamente quando il nome del registro esegue l'overload di un nome di variabile. Se il nome del registro è uguale a un nome di variabile nell'ambito corrente, il debugger lo interpreta come nome di variabile. In questo caso, è opportuno usare `$`*registername* o `@`*registername*.|
|`$clk`|Consente di visualizzare il tempo in cicli di orologio.|
|`$user`|Consente di visualizzare una struttura con le informazioni sull'account in cui viene eseguita l'applicazione. Per motivi di sicurezza non vengono visualizzate informazioni sulla password.|
|`$exceptionstack`|Visualizza la traccia dello stack dell'eccezione corrente di Windows Runtime. `$ exceptionstack` funziona solo nelle app UWP. `$ exceptionstack` non è supportata per C++ le eccezioni SEH e|
|`$returnvalue`|Visualizza il valore restituito di un metodo .NET.|

 In C# è possibile usare il pseudo variabili riportate illustrato nella tabella seguente:

|Pseudo variabile|Funzione|
|--------------------|--------------|
|`$exception`|Visualizza informazioni sull'ultima eccezione. Se non si è verificata alcuna eccezione, la valutazione di `$exception` produce un messaggio di errore.<br /><br /> Quando la finestra informazioni sulle eccezioni è disabilitata, `$exception` viene aggiunto automaticamente alla finestra **variabili locali** quando si verifica un'eccezione.|
|`$user`|Consente di visualizzare una struttura con le informazioni sull'account in cui viene eseguita l'applicazione. Per motivi di sicurezza non vengono visualizzate informazioni sulla password.|
|`$returnvalue`|Visualizza il valore restituito di un metodo .NET.|

 In Visual Basic, è possibile usare le pseudo variabili riportate nella tabella seguente:

|Pseudo variabile|Funzione|
|--------------------|--------------|
|`$exception`|Visualizza informazioni sull'ultima eccezione. Se non si è verificata alcuna eccezione, la valutazione di `$exception` produce un messaggio di errore.|
|`$delete` o `$$delete`|Elimina una variabile implicita creata nella finestra **Immediata**. La sintassi *è `$delete,` variabile* o `$delete,` *variabile* `.`|
|`$objectids` o `$listobjectids`|Visualizza tutti gli ID oggetto attivi come figli dell'espressione specificata. La sintassi *è `$objectid,` espressione* o *espressione* `$listobjectids,` `.`|
|`$` *N* `#`|Visualizza l'oggetto con ID dell'oggetto uguale a *N*.|
|`$dynamic`|Visualizza il nodo **Visualizzazione dinamica** speciale per un oggetto che implementa `IDynamicMetaObjectProvider`. Interfaccia. La sintassi è `$dynamic,` *object*. Questa funzionalità si applica solo al codice che usa .NET Framework versione 4 o successiva.|

## <a name="see-also"></a>Vedere anche
- [Finestre Espressioni di controllo e Controllo immediato](../debugger/watch-and-quickwatch-windows.md)
- [Finestra delle variabili](../debugger/debugger-windows.md)
