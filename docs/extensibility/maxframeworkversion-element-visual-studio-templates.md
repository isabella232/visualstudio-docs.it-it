---
title: Elemento MaxFrameworkVersion (modelli di Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento MaxFrameworkVersion e sul modo in cui specifica la versione massima del .NET Framework richiesta dal modello.
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
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090616"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Elemento MaxFrameworkVersion (modelli di Visual Studio)

Specifica la versione massima del .NET Framework richiesta dal modello. Determina il valore più alto disponibile nell'elenco a discesa **versione Framework di destinazione** della finestra di dialogo **nuovo progetto** . Affinché gli utenti possano selezionare una versione del Framework, è necessario specificare anche [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) come versione minima .NET Framework per il modello.

> [!IMPORTANT]
> A partire da Visual Studio 2017 versione 15,6, l'elenco a discesa **versione Framework di destinazione** non è più un filtro per i modelli visualizzati nella sezione **modelli** della finestra di dialogo **nuovo progetto** . Al contrario, l'elenco a discesa **versione Framework di destinazione** funziona come selezione Framework per il modello selezionato.

 \<VSTemplate> \<TemplateData>
 \<MaxFrameworkVersion>

## <a name="syntax"></a>Sintassi

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Categorizza il modello e ne definisce la modalità di visualizzazione nella finestra di dialogo **nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo deve essere il numero di versione più alto del .NET Framework consentito dal modello.

## <a name="remarks"></a>Commenti

`MaxFrameworkVersion` è un elemento facoltativo. L' `MaxFrameworkVersion` elemento deve essere omesso a meno che non sia necessario, in modo da non limitare inavvertitamente l'intervallo supportato di versioni .NET Framework per il modello. Deve inoltre essere omesso se .NET Framework non è applicabile al modello.

## <a name="example"></a>Esempio

Nell'esempio seguente vengono illustrati i metadati per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modello di classe standard.

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

In questo esempio, la versione massima del .NET Framework richiesta dal modello, rappresentata da `MaxFrameworkVersion` , è 4.7.1. Un progetto creato con questo modello può avere come destinazione .NET Framework versioni fino a 4.7.1.

## <a name="see-also"></a>Vedi anche

- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
