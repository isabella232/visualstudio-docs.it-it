---
title: '&lt;&gt;elemento document (sviluppo per Office in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 36d822d60d1a28d48f660f6d358b75bf4a913048
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "63000033"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento document (sviluppo per Office in Visual Studio)
  L' `document` elemento dello `vstov4` spazio dei nomi archivia informazioni specifiche della personalizzazione per le personalizzazioni a livello di documento.

## <a name="syntax"></a>Sintassi

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 Obbligatorio solo per le personalizzazioni a livello di documento. L'elemento `document` si trova nello spazio dei nomi `vstov4` . L'elemento `document` presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`solutionId`|Obbligatorio. GUID utilizzato dal Strumenti di Visual Studio per Office Runtime per identificare in modo univoco una soluzione a livello di documento. Questo valore viene archiviato come _AssemblyLocation proprietà personalizzata del documento. Per altre informazioni, vedere [Cenni preliminari sulle proprietà personalizzate dei documenti](../vsto/custom-document-properties-overview.md).|

 `document` è privo di elementi figlio.

## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento

### <a name="description"></a>Descrizione
 Nell'esempio di codice seguente viene illustrato l' `document` elemento in una soluzione Office a livello di documento distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Vedere anche

- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)