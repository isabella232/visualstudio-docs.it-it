---
title: Elemento DefaultName (modelli di Visual Studio) Documenti Microsoft
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
ms.openlocfilehash: 92bd29824cf1d3b91a7bdaa7220479c583ad0f23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712312"
---
# <a name="defaultname-element-visual-studio-templates"></a>Elemento DefaultName (modelli di Visual Studio)
Specifica il nome che il sistema del progetto di Visual Studio genererà per il progetto o l'elemento al momento della creazione.

 \<VSTemplate \<> TemplateData> \<DefaultName>

## <a name="syntax"></a>Sintassi

```
<DefaultName>
    Default Project Name
</DefaultName>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Questo testo specifica il nome predefinito del progetto o dell'elemento.

## <a name="remarks"></a>Osservazioni
 `DefaultName` è un elemento facoltativo.

 Per i progetti, questo elemento specifica il nome della directory in cui è archiviato il progetto su disco. Per gli elementi, specifica il nome del file di origine.

 Quando si crea un progetto o un elemento, è possibile modificare il nome predefinito utilizzando l'opzione **Nome,** disponibile nella finestra di dialogo **Nuovo progetto** o Aggiungi **nuovo elemento.**

 Se non si desidera che il sistema del progetto generi il nome predefinito per `False`il progetto o l'elemento, impostare l'elemento [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) su .

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] per il modello di elemento standard per una classe.

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
- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
