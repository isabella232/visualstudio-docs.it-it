---
title: Elemento DefaultName (modelli di Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento DefaultName e su come viene specificato il nome che verrà generato dal sistema di progetto di Visual Studio per il progetto o l'elemento al momento della creazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23defc424d3e7ed5095f0e29d673c191c755f9ce
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672730"
---
# <a name="defaultname-element-visual-studio-templates"></a>Elemento DefaultName (modelli di Visual Studio)
Specifica il nome che verrà generato dal sistema di progetto di Visual Studio per il progetto o l'elemento al momento della creazione.

 \<VSTemplate> \<TemplateData>
 \<DefaultName>

## <a name="syntax"></a>Sintassi

```
<DefaultName>
    Default Project Name
</DefaultName>
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

 Questo testo specifica il nome predefinito del progetto o dell'elemento.

## <a name="remarks"></a>Commenti
 `DefaultName` è un elemento facoltativo.

 Per i progetti, questo elemento specifica il nome della directory in cui è archiviato il progetto su disco. Per gli elementi, specifica il nome file del file di origine.

 Quando si crea un progetto o un elemento, è possibile modificare il nome predefinito utilizzando l'opzione **nome** , disponibile nella finestra di dialogo **nuovo progetto** o **Aggiungi nuovo elemento** .

 Se non si desidera che il sistema del progetto generi il nome predefinito per il progetto o l'elemento, impostare l'elemento [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) su `False` .

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per il modello di elemento standard per una [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] classe.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedere anche
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
