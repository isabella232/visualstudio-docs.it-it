---
description: L'elemento entryPoints dello spazio dei nomi vstav3 contiene tutti gli elementi entryPoint associati a una Office soluzione.
title: '&lt;Elemento entryPoints &gt; (Office sviluppo in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoints> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f41608335ecefa59ae78f04339cbb1f47d5e6a0f996b3052be6162206cc333b2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424359"
---
# <a name="ltentrypointsgt-element-office-development-in-visual-studio"></a>&lt;Elemento entryPoints &gt; (Office sviluppo in Visual Studio)
  L'elemento `entryPoints` dello spazio dei nomi `vstav3` contiene tutti gli elementi `entryPoint` associati a una soluzione Office.

## <a name="syntax"></a>Sintassi

```xml
<entryPoints>
    <entryPoint>
    </entryPoint>
    <entryPoint>
    </entryPoint>
    <entryPoint>
    </entryPoint>
</entryPoints>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `entryPoints` è obbligatorio e si trova nello spazio dei nomi `vstav3` . Per ogni soluzione Office è definito un elemento `entryPoints` in un manifesto dell'applicazione. Ad esempio, se si distribuiscono tre soluzioni Office in una distribuzione multiprogetto, nel manifesto dell'applicazione sono presenti tre elementi `entryPoints` .

 L'elemento `entryPoints` presenta l'attributo seguente:

|Attributo|Descrizione|
|---------------|-----------------|
|id|Necessario per la distribuzione multiprogetto. Il nome della soluzione Office. L'id non può contenere il simbolo uguale (=).|

 `entryPoints` presenta gli elementi seguenti:

### <a name="entrypoint"></a>entryPoint
 Obbligatorio. Il ruolo dell'elemento nello spazio dei nomi è definito `entryPoint` `vstav3` in&#60;[entryPoint ](../vsto/entrypoint-element-office-development-in-visual-studio.md)&#62; elemento &#40;Office sviluppo in Visual Studio&#41;.

## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra l'elemento `entryPoints` in un manifesto dell'applicazione per una soluzione a livello di documento distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstav3:entryPoints>
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
</vstav3:entryPoints>
```

## <a name="vsto-add-in-example"></a>VSTO Esempio di componente aggiuntivo

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra un elemento `entryPoints` in un manifesto dell'applicazione per una soluzione a livello di applicazione distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstav3:entryPoints>
  <vstav3:entryPoint
    class="ContosoOutlookAddIn.ThisAddIn">
    <assemblyIdentity
      name="ContosoOutlookAddIn"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
</vstav3:entryPoints>
```

## <a name="multi-project-deployment-example"></a>Esempio di distribuzione multi-progetto

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra l'elemento `entryPoints` in un manifesto dell'applicazione per una distribuzione di più progetti. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstav3:entryPoints
  id="ContosoExcel">
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
</vstav3:entryPoints>
<vstav3:entryPoints
  id="ContosoOutlook">
  <vstav3:entryPoint
    class="ContosoOutlookAddIn.ThisAddIn">
    <assemblyIdentity
      name="ContosoOutlookAddIn"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
</vstav3:entryPoints>
```

## <a name="see-also"></a>Vedi anche

- [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
