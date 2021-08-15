---
title: Elemento SupportsMasterPage (Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento SupportsMasterPage e su come specifica se la casella di controllo Seleziona pagina master è abilitata o meno nella finestra di dialogo Aggiungi nuovo elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4138f7ffdb227c0a7bacd09fb514d2d22c63d5962ab3c9787b616dedde3d8d38
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121320973"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>Elemento SupportsMasterPage (modelli di Visual Studio)
Specifica se la casella di controllo **Seleziona pagina master** è abilitata nella finestra **di** dialogo Aggiungi nuovo elemento .

 \<VSTemplate> \<TemplateData>
 \<SupportsMasterPage>

## <a name="syntax"></a>Sintassi

```
<SupportsMasterPage> true/false </SupportsMasterPage>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Specifica i dati che classificano il modello e ne definisce la modalità di visualizzazione nella finestra **di dialogo Project** o **Nuovo** elemento .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo deve essere o , che indica se la casella di controllo Seleziona pagina master è abilitata nella finestra di dialogo `true` `false` Aggiungi nuovo elemento .  

## <a name="remarks"></a>Commenti
 `SupportsMasterPage` è un elemento facoltativo. Il valore predefinito è `false`.

 `SupportsMasterPage`L'elemento è disponibile solo per i modelli di elemento Web.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per un progetto Web che include il supporto per una pagina master.

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsMasterPage>true</SupportsMasterPage>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedi anche
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
