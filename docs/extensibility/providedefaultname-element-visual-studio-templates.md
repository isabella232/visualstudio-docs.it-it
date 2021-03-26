---
title: Elemento ProvideDefaultName (modelli di Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento ProvideDefaultName e su come specifica se Visual Studio genererà un nome predefinito di Visual Studio nella finestra di dialogo Aggiungi nuovo elemento o nuovo progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d29ca3075ee6e5ef031bb360ecfd10d6cb341c26
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068635"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Elemento ProvideDefaultName (modelli di Visual Studio)
Specifica se il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sistema del progetto genererà un nome predefinito per il modello nella finestra di dialogo **Aggiungi nuovo elemento** o **nuovo progetto** .

 \<VSTemplate> \<TemplateData>
 \<ProvideDefaultName>

## <a name="syntax"></a>Sintassi

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
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

 Il testo deve essere `true` o `false` , che indica se generare o meno un nome predefinito per il modello nella finestra di **dialogo Aggiungi nuovo elemento** o **nuovo progetto** .

## <a name="remarks"></a>Commenti
 `ProvideDefaultName` è un elemento facoltativo. Il valore predefinito è `true`.

 Se l' `ProvideDefaultName` elemento è `false` , le caselle **nome** della finestra di dialogo **Aggiungi nuovo elemento** e **nuovo progetto** contengono il valore `<Enter_name>` .

 Usare l'elemento [defaultName](../extensibility/defaultname-element-visual-studio-templates.md) per specificare il nome predefinito del progetto o dell'elemento nelle finestre di dialogo **Aggiungi nuovo elemento** e **nuovo progetto** . Quando il valore dell' `ProvideDefaultName` elemento è `true` , l'omissione dell' `DefaultName` elemento per i progetti popola la finestra di dialogo con il nome del modello, ossia il valore dell'elemento [Name](../extensibility/name-element-visual-studio-templates.md) .

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente l' `ProvideDefaultName` elemento viene impostato su `false` .

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

## <a name="see-also"></a>Vedi anche
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
