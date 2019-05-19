---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 26d9169be242990b9ca99b4fe4fe043d56fb7f30
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65839647"
---
Dovrebbe essere possibile eseguire il debug del codice con i simboli generati nel computer di Visual Studio. L'uso di simboli locali consente di migliorare notevolmente le prestazioni del debugger remoto.  Se è necessario usare simboli remoti, indicare a Remote Debugging Monitor di eseguire la ricerca di simboli nel computer remoto.  

A partire da Visual Studio 2013 Update 2 è possibile usare la seguente opzione della riga di comando di msvsmon per usare i simboli remoti per il codice gestito: `Msvsmon /FallbackLoadRemoteManagedPdbs`  

Per altre informazioni, vedere le informazioni della Guida sul debug remoto (premere **F1** nella finestra del debugger remoto oppure fare clic su **? > Utilizzo**). Altre informazioni sono disponibili nel post del blog [.NET Remote Symbol Loading Changes in Visual Studio 2012 and 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx) (Modifiche nel caricamento remoto dei simboli .NET in Visual Studio 2012 e 2013).
