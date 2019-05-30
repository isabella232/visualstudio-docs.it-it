---
title: Elemento ProvideDefaultName (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2a19d6a93b709128e8750b6cea82d067b77db98
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335815"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Elemento ProvideDefaultName (modelli di Visual Studio)
Specifica se il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sistema di progetto verrà generato un nome predefinito per il modello nella **Aggiungi nuovo elemento** o **nuovo progetto** nella finestra di dialogo.

 \<VSTemplate> \<TemplateData> \<ProvideDefaultName>

## <a name="syntax"></a>Sintassi

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
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

 Il testo deve essere `true` o `false`, che indica se generare un nome predefinito per il modello nella o meno la **Aggiungi nuovo elemento** o **nuovo progetto** nella finestra di dialogo.

## <a name="remarks"></a>Note
 `ProvideDefaultName` è un elemento facoltativo. Il valore predefinito è `true`.

 Se il `ProvideDefaultName` elemento viene `false`, il **nome** caselle del **Aggiungi nuovo elemento** e **nuovo progetto** finestre di dialogo contengono il valore `<Enter_name>`.

 Usare il [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) elemento per specificare il nome predefinito del progetto o elemento il **Aggiungi nuovo elemento** e **nuovo progetto** finestre di dialogo. Quando il valore del `ProvideDefaultName` elemento viene `true`, omissione del `DefaultName` (elemento) per i progetti popola la finestra di dialogo con il nome del modello, vale a dire, il valore dal [nome](../extensibility/name-element-visual-studio-templates.md) elemento.

## <a name="example"></a>Esempio
 I seguente esempio di codice impostare il `ProvideDefaultName` elemento `false`.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProvideDefaultName>false</ProvideDefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedere anche
- [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
