---
title: Interfaccia Excel Communicator di esempio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 88aa282a2e742ffff53582fd4855d06e3a06db69
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="sample-excel-communicator-interface"></a>Interfaccia Excel Communicator di esempio
L'interfaccia `IExcelUICommunication` di esempio viene usata nell'oggetto `ExcelUICommunicator` del progetto `ExcelAddIn`.

## <a name="iexceluicommunication-interface"></a>Interfaccia IExcelUICommunication
 Questa interfaccia definisce i punti di comunicazione tra `CodedUIExtension`, che viene eseguito nel processo del test codificato dell'interfaccia utente, e `ExcelCodedUIAddIn`, che viene eseguito nel processo [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].

 L'assembly `ExcelCodedUIAddinHelper` contiene una classe `ExcelUICommunicator` che deriva da questa interfaccia e usa il modello a oggetti di Excel per elaborare i metodi.

 Alcuni metodi ottengono le informazioni richieste da Excel, quindi creano e restituiscono uno degli oggetti informazioni, ad esempio l'oggetto `CellInformation`.

 Altri metodi usano un oggetto informazioni fornito, trovano il controllo corrispondente in Excel ed eseguono alcune operazioni di elaborazione sul controllo. Ad esempio, il metodo `ScrollIntoView` scorre il foglio di lavoro in modo da rendere visibile la cella designata.

## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>Comunicazione di CodedUIExtensibilitySample ed ExcelCodedUIAddinHelper
 L'assembly `ExcelCodedUIAddinHelper` viene eseguito nel processo di Excel e contiene la classe `UICommunicator`, che implementa l'interfaccia `IExcelUITestCommunication` e ottiene o imposta le informazioni richieste direttamente dall'interfaccia utente di Excel.

 L'assembly `CodedUIExtensibilitySample` viene eseguito nel processo del test codificato dell'interfaccia utente di Visual Studio. Questo assembly contiene la classe `Communicator` che apre un canale di Servizi remoti .NET e fornisce una proprietà `Instance` che usa l'interfaccia `IExcelUICommunication` in modo da usare l'oggetto `UICommunicator` nell'assembly `ExcelCodedUIAddinHelper` per passare le richieste e gli oggetti informazioni, ad esempio un oggetto `CellInformation`, tra i due assembly.

## <a name="see-also"></a>Vedere anche

- [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
- [Componente aggiuntivo di Excel di esempio per i test codificati dell'interfaccia utente](../test/sample-excel-add-in-for-coded-ui-testing.md)
- [Estensione di esempio per i test codificati dell'interfaccia utente per Excel](../test/sample-coded-ui-test-extension-for-excel.md)
