---
title: Elemento MaxFrameworkVersion (modelli Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento MaxFrameworkVersion e su come specifica la versione massima del .NET Framework richiesta dal modello.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 05d61e298c666d22df1af8d426cb0671feb8b9c5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709451"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Elemento MaxFrameworkVersion (Visual Studio modelli)

Specifica la versione massima del .NET Framework richiesta dal modello. Determina il valore più alto disponibile nell'elenco a discesa **Versione framework** di destinazione della finestra di Project finestra **di** dialogo. Per consentire agli utenti di selezionare una versione del framework, è necessario specificare [anche RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) come versione .NET Framework minima per il modello.

> [!IMPORTANT]
> A partire da Visual Studio 2017 versione 15.6, l'elenco a discesa Versione  **framework** di destinazione non è più un filtro per i modelli visualizzati nella sezione Modelli della finestra di dialogo Nuovo **Project.** L'elenco a discesa **Versione framework di** destinazione funziona invece come selezione framework per il modello selezionato.

 \<VSTemplate> \<TemplateData>
 \<MaxFrameworkVersion>

## <a name="syntax"></a>Sintassi

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Categorizza il modello e definisce come viene visualizzato nella finestra di dialogo Nuovo **Project** o Aggiungi **nuovo** elemento.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo deve essere il numero di versione più alto del .NET Framework consentito dal modello.

## <a name="remarks"></a>Commenti

`MaxFrameworkVersion` è un elemento facoltativo. L'elemento deve essere omesso a meno che non sia obbligatorio, in modo da non limitare inavvertitamente l'intervallo supportato di versioni .NET Framework `MaxFrameworkVersion` per il modello. Deve inoltre essere omesso se .NET Framework non è applicabile al modello.

## <a name="example"></a>Esempio

Nell'esempio seguente vengono illustrati i metadati per un modello [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] di classe standard.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

In questo esempio la versione massima del .NET Framework richiesta dal modello, rappresentata da `MaxFrameworkVersion` , è 4.7.1. Un progetto creato con questo modello può essere .NET Framework versioni fino alla 4.7.1.

## <a name="see-also"></a>Vedi anche

- [Visual Studio riferimento allo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto ed elemento](../ide/creating-project-and-item-templates.md)
