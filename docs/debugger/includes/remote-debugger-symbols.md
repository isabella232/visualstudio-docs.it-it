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
ms.openlocfilehash: c1f51f1b5540eb3272998583a4ff7d86ce9c8e3d907f0ecabb73eff884575a84
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "122058295"
---
Dovrebbe essere possibile eseguire il debug del codice con i simboli generati nel computer di Visual Studio. L'uso di simboli locali consente di migliorare notevolmente le prestazioni del debugger remoto.  Se è necessario usare simboli remoti, indicare a Remote Debugging Monitor di eseguire la ricerca di simboli nel computer remoto.  

A partire da Visual Studio 2013 Update 2 è possibile usare la seguente opzione della riga di comando di msvsmon per usare i simboli remoti per il codice gestito: `Msvsmon /FallbackLoadRemoteManagedPdbs`  

Per altre informazioni, vedere le informazioni della Guida sul debug remoto (premere **F1** nella finestra del debugger remoto oppure fare clic su **? > Utilizzo**). Altre informazioni sono disponibili nel post del blog [.NET Remote Symbol Loading Changes in Visual Studio 2012 and 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/) (Modifiche nel caricamento remoto dei simboli .NET in Visual Studio 2012 e 2013).
