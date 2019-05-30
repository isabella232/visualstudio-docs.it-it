---
title: Elemento SupportsLanguageDropDown (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6dbc2c5cae40078f033fa0fb85c6fda032e8ec4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316809"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>Elemento SupportsLanguageDropDown (modelli di Visual Studio)
Specifica se il modello di elemento Web è identico per più linguaggi e, se il **Language** opzione è abilitata nel **Aggiungi nuovo elemento** nella finestra di dialogo.

 \<VSTemplate > \<TemplateData > \<SupportsLanguageDropDown >

## <a name="syntax"></a>Sintassi

```
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

 Il testo deve essere `true` o `false`, che indica o meno la **Language** opzione è disponibile il **Aggiungi nuovo elemento** nella finestra di dialogo.

## <a name="remarks"></a>Note
 `SupportsLanguageDropDown` è un elemento facoltativo. Il valore predefinito è `false`.

 Il `SupportsLanguageDropDown` elemento è disponibile solo per i modelli di elemento di Web.

 Se il valore per questo elemento è impostato su `true`, quindi il modello di elemento è identico per tutti i linguaggi di programmazione e il **Language** opzione è abilitata nel **Aggiungi nuovo elemento** nella finestra di dialogo. Questa opzione consente di scegliere il linguaggio di programmazione del nuovo elemento che si desidera creare dal modello.

## <a name="example"></a>Esempio
 L'esempio seguente specifica per visualizzare il **linguaggio** elenco a discesa di opzione.

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

## <a name="see-also"></a>Vedere anche
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)