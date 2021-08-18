---
description: L'elemento documento dello spazio dei nomi vstov4 archivia informazioni specifiche della personalizzazione per le personalizzazioni a livello di documento.
title: '&lt;Elemento &gt; document (Office sviluppo in Visual Studio)'
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 66ef774db63c01a1b622c6ea937bd29444bc3d71
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148298"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;Elemento &gt; document (Office sviluppo in Visual Studio)
  `document`L'elemento dello spazio dei nomi archivia informazioni specifiche della `vstov4` personalizzazione per le personalizzazioni a livello di documento.

## <a name="syntax"></a>Sintassi

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 Obbligatorio solo per le personalizzazioni a livello di documento. L'elemento `document` si trova nello spazio dei nomi `vstov4` . L'elemento `document` presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`solutionId`|Obbligatorio. GUID usato dal runtime Visual Studio Tools per Office per identificare in modo univoco una soluzione a livello di documento. Questo valore viene archiviato come proprietà _AssemblyLocation personalizzata del documento. Per altre informazioni, vedere [Panoramica delle proprietà personalizzate dei documenti.](../vsto/custom-document-properties-overview.md)|

 `document` è privo di elementi figlio.

## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento

### <a name="description"></a>Descrizione
 Nell'esempio di codice seguente viene illustrato l'elemento in una soluzione Office `document` a livello di documento distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Questo esempio di codice fa parte di un esempio più ampio fornito in [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Vedi anche

- [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
