---
title: Interfaccia Excel Communicator di esempio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e3a9bd037c8886743910af649bf831b11337598
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660496"
---
# <a name="sample-excel-communicator-interface"></a>Interfaccia Excel Communicator di esempio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'interfaccia `IExcelUICommunication` di esempio viene usata nell'oggetto `ExcelUICommunicator` del progetto `ExcelAddIn`.

## <a name="iexceluicommunication-interface"></a>Interfaccia IExcelUICommunication
 Questa interfaccia definisce i punti di comunicazione tra `CodedUIExtension`, che viene eseguito nel processo del test codificato dell'interfaccia utente, e `ExcelCodedUIAddIn`, che viene eseguito nel processo [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].

 L'assembly `ExcelCodedUIAddinHelper` contiene una classe `ExcelUICommunicator` che deriva da questa interfaccia e usa il modello a oggetti di Excel per elaborare i metodi.

 Alcuni metodi ottengono le informazioni richieste da Excel, quindi creano e restituiscono uno degli oggetti informazioni, ad esempio l'oggetto `CellInformation`.

 Altri metodi usano un oggetto informazioni fornito, trovano il controllo corrispondente in Excel ed eseguono alcune operazioni di elaborazione sul controllo. Ad esempio, il metodo `ScrollIntoView` scorre il foglio di lavoro in modo da rendere visibile la cella designata.

## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>Comunicazione di CodedUIExtensibilitySample ed ExcelCodedUIAddinHelper
 L'assembly `ExcelCodedUIAddinHelper` viene eseguito nel processo di Excel e contiene la classe `UICommunicator`, che implementa l'interfaccia `IExcelUITestCommunication` e ottiene o imposta le informazioni richieste direttamente dall'interfaccia utente di Excel.

 L'assembly `CodedUIExtensibilitySample` viene eseguito nel processo del test codificato dell'interfaccia utente di Visual Studio. Questo assembly contiene la classe `Communicator` che apre un canale di Servizi remoti .NET e fornisce una proprietà `Instance` che usa l'interfaccia `IExcelUICommunication` in modo da usare l'oggetto `UICommunicator` nell'assembly `ExcelCodedUIAddinHelper` per passare le richieste e gli oggetti informazioni, ad esempio un oggetto `CellInformation`, tra i due assembly.

## <a name="see-also"></a>Vedere anche
 Estensione [di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md) il [componente aggiuntivo Excel](../test/sample-excel-add-in-for-coded-ui-testing.md) di esempio di Microsoft Excel per il test codificato dell'interfaccia utente estensione di [test codificato dell'interfaccia utente per Excel](../test/sample-coded-ui-test-extension-for-excel.md)
