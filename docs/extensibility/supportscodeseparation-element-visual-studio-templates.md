---
title: SupportsCodeSeparation Elemento (modelli di Visual Studio) . Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd52ae47f47f3ca1fce23f7cf8d37260ec86fb0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699506"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>Elemento SupportsCodeSeparation (modelli di Visual Studio)
Specifica se la casella di controllo **Inserisci codice in file separato** è attivata nella finestra di dialogo Aggiungi nuovo **elemento.**

 \<VSTemplate \<> TemplateData> \<supporta la> CodeSeparation

## <a name="syntax"></a>Sintassi

```
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 No.

### <a name="child-elements"></a>Elementi figlio
 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Categorizza il modello e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Nuovo elemento.**|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo deve `true` `false`essere o , che indica se la casella di controllo **Inserisci codice in un file separato** è attivata nella finestra di dialogo Aggiungi nuovo **elemento** .

## <a name="remarks"></a>Osservazioni
 `SupportsCodeSeparation` è un elemento facoltativo. Il valore predefinito è `false`.

 L'elemento `SupportsCodeSeparation` è disponibile solo per i modelli di elemento Web.

 La separazione del codice, o il modello di pagina code-behind, consente di mantenere il markup in un file e il codice di programmazione in un altro file. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]e altri linguaggi .NET utilizzano questo modello.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene specificato di visualizzare l'opzione **Inserisci codice in file separato.**

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

## <a name="see-also"></a>Vedere anche
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
