---
title: Elemento ProvideDefaultName (modelli Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento ProvideDefaultName e su come specifica se Visual Studio genererà un nome Visual Studio predefinito nella finestra di dialogo Aggiungi nuovo elemento o Project nuovo elemento.
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
ms.openlocfilehash: 0415e44f891b78908c27ef14627582ca7c217bdcf6382ffc6185db310c556b49
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400913"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Elemento ProvideDefaultName (Visual Studio personalizzati)
Specifica se il sistema del progetto genererà un nome predefinito per il modello nella finestra di dialogo Aggiungi nuovo elemento [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **o Project** progetto. 

 \<VSTemplate> \<TemplateData>
 \<ProvideDefaultName>

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

 Il testo deve essere o , che indica se generare o meno un nome predefinito per il modello nella finestra di dialogo `true` Aggiungi nuovo elemento `false` **Project** nuovo elemento. 

## <a name="remarks"></a>Commenti
 `ProvideDefaultName` è un elemento facoltativo. Il valore predefinito è `true`.

 Se `ProvideDefaultName` l'elemento è `false` , **le caselle Nome** delle finestre di   dialogo Aggiungi nuovo elemento e Project finestra di dialogo contengono il valore `<Enter_name>` .

 Usare [l'elemento DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) per specificare il nome  predefinito del progetto o dell'elemento nelle finestre di dialogo Aggiungi nuovo elemento **e Project** nuovo elemento. Quando il valore `ProvideDefaultName` `true` dell'elemento è , l'omissione dell'elemento per i progetti popola la finestra di dialogo con il nome del modello, cio' il valore `DefaultName` [dell'elemento Name.](../extensibility/name-element-visual-studio-templates.md)

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente `ProvideDefaultName` l'elemento viene impostato su `false` .

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
- [Visual Studio sullo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
