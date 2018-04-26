---
title: 'Estensione Excel di esempio: classe PropertyProvider'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e4a1e96fc666275d83cf0f32edf00f0fc2f6c03c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Estensione Excel di esempio: classe PropertyProvider
Questa classe interna estende la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> e fornisce servizi di proprietà per gli elementi di [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] per la registrazione e la riproduzione dei test dell'interfaccia utente.

## <a name="getcontrolsupportlevel-method"></a>Metodo GetControlSupportLevel
 Il metodo <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> restituisce un numero che indica il livello di supporto che il provider di proprietà può offrire per il controllo specificato. Più alto è il valore restituito, maggiore è il livello di supporto del controllo offerto dal provider di proprietà. In questo caso, il metodo controlla il valore della proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> del controllo specificato. Se il valore è "Excel" e <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> indica che si tratta di un `CellElement`, il metodo restituisce il valore più elevato. In caso contrario, restituisce zero, che indica che non viene fornito alcun supporto.

## <a name="getpropertynames-method"></a>Metodo GetPropertyNames
 Restituisce un dizionario di nomi di proprietà e descrittori di proprietà per le proprietà supportate di un controllo di cella di Excel.

## <a name="getpropertydescriptor-method"></a>Metodo GetPropertyDescriptor
 Questo metodo viene chiamato dal framework di test per ottenere il descrittore di proprietà predefinito per il nome di proprietà specificato.

## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>Metodi GetPropertyValue e SetPropertyValue
 Il metodo `GetPropertyValue` usa la classe `Communicator` dell'estensione per restituire il valore della proprietà da Excel. Il metodo `SetPropertyValue` usa la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> e il componente `Communicator` per impostare il valore della proprietà. Questi metodi vengono chiamati dal framework di test.

## <a name="code-generation-customization-methods"></a>Metodi di personalizzazione della generazione di codice
 Questi metodi non sono implementati per questa estensione. Di conseguenza, restituiscono `null` o generano l'eccezione <xref:System.NotImplementedException>.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>
- [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
