---
description: Ogni elemento entryPoint dello spazio dei nomi vstav3 identifica un assembly di personalizzazione che deve essere eseguito ClickOnce'applicazione.
title: '&lt;Elemento entryPoint &gt; (Office sviluppo in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ff0f3313da0479c7ec6a8dda0c2bc609e6f7b4a357821b9acf988e7ff599112a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424346"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;Elemento entryPoint &gt; (Office sviluppo in Visual Studio)
  Ogni elemento `entryPoint` dello spazio dei nomi `vstav3` identifica un assembly di personalizzazione che deve essere eseguito quando l'applicazione [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] è installata.

## <a name="syntax"></a>Sintassi

```xml
<entryPoint class>
    <assemblyIdentity />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `entryPoint` è obbligatorio e si trova nello spazio dei nomi `vstav3` .

 Ogni elemento `entryPoint` può contenere solo un assembly di personalizzazione. Possono essere definiti più elementi `entryPoint` in un manifesto dell'applicazione.

 L'elemento `entryPoint` presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`class`|Obbligatorio. Identifica un assembly di personalizzazione da eseguire. La sintassi per questo attributo è *NamespaceName.ClassName*.|

 `entryPoint` presenta l'elemento seguente:

### <a name="assemblyidentity"></a>assemblyIdentity
 Obbligatorio. L'elemento `assemblyIdentity` nello spazio dei nomi `vstav3` si riferisce a un elemento `assemblyIdentity` esistente nel manifesto dell'applicazione [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .

 Il ruolo di e dei relativi attributi `assemblyIdentity` è definito in&#60;[assemblyIdentity&#62;'&#40;ClickOnce'&#41;](../deployment/assemblyidentity-element-clickonce-application.md).

## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra elementi `entryPoint` in un manifesto dell'applicazione per una soluzione Office a livello di documento distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più ampio fornito in [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstav3:entryPoint
  class="ContosoExcelWorkbook.ThisWorkbook">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet1">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet2">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet3">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="vsto-add-in-example"></a>VSTO Esempio di componente aggiuntivo

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra un elemento `entryPoint` in un manifesto dell'applicazione per una soluzione Office a livello di applicazione distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più ampio fornito in [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstav3:entryPoint
  class="ContosoOutlookAddIn.ThisAddIn">
  <assemblyIdentity
    name="ContosoOutlookAddIn"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="see-also"></a>Vedi anche

- [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
