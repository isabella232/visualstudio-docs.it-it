---
title: Elemento SupportsLanguageDropDown (modelli di Visual Studio)
titleSuffix: ''
description: Informazioni sull'elemento SupportsLanguageDropDown e su come specifica se il modello di elemento Web è identico per più lingue e se l'opzione Language è abilitata.
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
ms.openlocfilehash: 67bf92c8c447faac2969bde3f208823158663712
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056077"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>Elemento SupportsLanguageDropDown (modelli di Visual Studio)

Specifica se il modello di elemento Web è identico per più lingue e se l'opzione **lingua** è abilitata nella finestra di dialogo **Aggiungi nuovo elemento** .

 \<VSTemplate> \<TemplateData>
 \<SupportsLanguageDropDown>

## <a name="syntax"></a>Sintassi

```xml
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

 Nessuna.

### <a name="child-elements"></a>Elementi figlio

 Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo

 È necessario specificare un valore di testo.

 Il testo deve essere `true` o `false` , che indica se l'opzione **lingua** è disponibile o meno nella finestra di dialogo **Aggiungi nuovo elemento** .

## <a name="remarks"></a>Commenti

 `SupportsLanguageDropDown` è un elemento facoltativo. Il valore predefinito è `false`.

 L' `SupportsLanguageDropDown` elemento è disponibile solo per i modelli di elemento Web.

 Se il valore di questo elemento è impostato su `true` , il modello di elemento è identico per tutti i linguaggi di programmazione e l'opzione **lingua** è abilitata nella finestra di dialogo **Aggiungi nuovo elemento** . Questa opzione consente di scegliere il linguaggio di programmazione del nuovo elemento che si desidera creare dal modello.

## <a name="example"></a>Esempio

 Nell'esempio seguente viene specificato di visualizzare l'opzione di riepilogo della **lingua** .

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
