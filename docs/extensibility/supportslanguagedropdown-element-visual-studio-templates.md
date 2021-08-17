---
title: Elemento SupportsLanguageDropDown (modelli di Visual Studio)
titleSuffix: ''
description: Informazioni sull'elemento SupportsLanguageDropDown e su come specifica se il modello di elemento Web è identico per più lingue e se l'opzione Lingua è abilitata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f02b7b70e3caedca11a41fd399ec80e84c4c8a39ccfc8eb98db795a4d49fa58b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413817"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>Elemento SupportsLanguageDropDown (modelli di Visual Studio)

Specifica se il modello di elemento Web è identico per più lingue e se l'opzione **Lingua** è abilitata nella finestra di dialogo Aggiungi **nuovo** elemento.

 \<VSTemplate> \<TemplateData>
 \<SupportsLanguageDropDown>

## <a name="syntax"></a>Sintassi

```xml
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo

 È necessario specificare un valore di testo.

 Il testo deve essere `true` o , che indica se l'opzione Lingua è disponibile nella finestra di dialogo Aggiungi `false` nuovo elemento .  

## <a name="remarks"></a>Commenti

 `SupportsLanguageDropDown` è un elemento facoltativo. Il valore predefinito è `false`.

 `SupportsLanguageDropDown`L'elemento è disponibile solo per i modelli di elemento Web.

 Se il valore di questo elemento è impostato su , il modello di elemento è identico per tutti i linguaggi di programmazione e l'opzione Linguaggio è abilitata nella finestra di dialogo `true` Aggiungi nuovo elemento .   Questa opzione consente di scegliere il linguaggio di programmazione del nuovo elemento che si vuole creare dal modello.

## <a name="example"></a>Esempio

 Nell'esempio seguente viene specificato di visualizzare **l'opzione a** discesa Lingua .

```xml
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>
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
