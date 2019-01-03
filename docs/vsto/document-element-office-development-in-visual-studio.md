---
title: '&lt;documento&gt; elemento (sviluppo per Office in Visual Studio)'
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2c1798815ee3216d6f3bb41eae70ae3e2cdc0121
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854756"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;documento&gt; elemento (sviluppo per Office in Visual Studio)
  Il `document` dell'elemento di `vstov4` dello spazio dei nomi archivia informazioni specifiche della personalizzazione per le personalizzazioni a livello di documento.

## <a name="syntax"></a>Sintassi

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Gli elementi e attributi
 Obbligatorio solo per le personalizzazioni a livello di documento. L'elemento `document` si trova nello spazio dei nomi `vstov4` . L'elemento `document` presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`solutionId`|Obbligatorio. Il GUID usato da Visual Studio Tools per Office runtime per identificare in modo univoco una soluzione a livello di documento. Questo valore viene archiviato come proprietà AssemblyLocation personalizzate dei documenti. Per altre informazioni, vedere [Cenni preliminari sulle proprietà di documento Custom](../vsto/custom-document-properties-overview.md).|

 `document` è privo di elementi figlio.

## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra il `document` elemento in una soluzione Office a livello di documento distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice è parte di un esempio più esaustivo disponibile nel [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Vedere anche

- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)