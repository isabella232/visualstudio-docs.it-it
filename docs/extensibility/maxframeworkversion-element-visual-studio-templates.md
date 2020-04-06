---
title: Elemento MaxFrameworkVersion (modelli di Visual Studio) Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3acf9c40499417fe180ce470224824cc89a113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702627"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Elemento MaxFrameworkVersion (modelli di Visual Studio)

Specifica la versione massima di .NET Framework richiesta dal modello. Determina il valore più alto disponibile nell'elenco a discesa **Versione framework** di destinazione della finestra di dialogo **Nuovo progetto.** Affinché gli utenti siano in grado di selezionare una versione del framework, è inoltre necessario specificare [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) come versione minima di .NET Framework per il modello.

> [!IMPORTANT]
> A partire da Visual Studio 2017 versione 15.6, l'elenco a discesa **Versione framework** di destinazione non è più un filtro per i modelli visualizzati nella sezione **Modelli** della finestra di dialogo **Nuovo progetto.** Al contrario, l'elenco a discesa **Versione framework** di destinazione funziona come una selezione framework per il modello selezionato.

 \<VSTemplate \<> TemplateData> \<> MaxFrameworkVersion

## <a name="syntax"></a>Sintassi

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Categorizza il modello e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o Aggiungi **nuovo elemento.**|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo deve essere il numero di versione più alto di .NET Framework consentito dal modello.

## <a name="remarks"></a>Osservazioni

`MaxFrameworkVersion` è un elemento facoltativo. L'elemento `MaxFrameworkVersion` deve essere omesso a meno che non sia necessario, in modo da non limitare inavvertitamente l'intervallo supportato di versioni di .NET Framework per il modello. Deve anche essere omesso se .NET Framework non è applicabile al modello.

## <a name="example"></a>Esempio

Nell'esempio seguente vengono illustrati [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] i metadati per un modello di classe standard.

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

In questo esempio, la versione massima di .NET Framework richiesta `MaxFrameworkVersion`dal modello, rappresentata da , è 4.7.1. Un progetto creato con questo modello può essere destinato alle versioni di .NET Framework fino alla 4.7.1.A project created with this template can target .NET Framework versions up to 4.7.1.

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
