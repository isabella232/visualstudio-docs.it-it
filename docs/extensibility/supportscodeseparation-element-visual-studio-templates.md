---
title: Elemento SupportsCodeSeparation (modelli di Visual Studio)
titleSuffix: ''
description: Informazioni sull'elemento SupportsCodeSeparation e su come specifica se la casella di controllo Inserisci codice in un file separato è abilitata nella finestra di dialogo Aggiungi nuovo elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a1f33f86722621b6c069363f3136a62b497ed5d31a78c2744f5432bea1c44832
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431448"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>Elemento SupportsCodeSeparation (modelli di Visual Studio)
Specifica se la casella di controllo **Inserisci codice in un file** separato è abilitata nella finestra **di** dialogo Aggiungi nuovo elemento .

 \<VSTemplate> \<TemplateData>
 \<SupportsCodeSeparation>

## <a name="syntax"></a>Sintassi

```
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello e ne definisce la modalità di visualizzazione nella finestra di **dialogo Project** o **Nuovo** elemento .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo deve essere o , che indica se la casella di controllo Inserisci codice in un file separato è abilitata nella finestra di dialogo `true` `false` Aggiungi nuovo elemento .  

## <a name="remarks"></a>Commenti
 `SupportsCodeSeparation` è un elemento facoltativo. Il valore predefinito è `false`.

 `SupportsCodeSeparation`L'elemento è disponibile solo per i modelli di elemento Web.

 La separazione del codice, o modello di pagina code-behind, consente di mantenere il markup in un file e il codice di programmazione in un altro file. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e altri linguaggi .NET usano questo modello.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene specificato di visualizzare **l'opzione Inserisci codice in un file** separato.

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
        <SupportsCodeSeparation>true</SupportsCodeSeparation>
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
