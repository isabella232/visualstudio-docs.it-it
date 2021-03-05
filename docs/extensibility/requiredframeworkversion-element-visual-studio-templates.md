---
description: Specifica la versione minima del .NET Framework richiesta dal modello.
title: Elemento RequiredFrameworkVersion (modelli di Visual Studio)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3700735f987da7320d569b2cee020f0d8a072bdc
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221796"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Elemento RequiredFrameworkVersion (modelli di Visual Studio)

Specifica la versione minima del .NET Framework richiesta dal modello. L'elenco a discesa **versione Framework di destinazione** verrà visualizzato nella finestra di dialogo **nuovo progetto** . L' `RequiredFrameworkVersion` elemento determina anche il valore più basso disponibile nell'elenco a discesa.

> [!IMPORTANT]
> A partire da Visual Studio 2017 versione 15,6, l'elenco a discesa **versione Framework di destinazione** non è più un filtro per i modelli visualizzati nella sezione **modelli** della finestra di dialogo **nuovo progetto** . Al contrario, l'elenco a discesa funziona come selezione del Framework per il modello selezionato.

 \<VSTemplate> \<TemplateData>
 \<RequiredFrameworkVersion>

## <a name="syntax"></a>Sintassi

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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

 Il testo deve essere il numero di versione minimo del .NET Framework necessario per il modello.

## <a name="remarks"></a>Commenti

`RequiredFrameworkVersion` è un elemento facoltativo. Utilizzare questo elemento solo se il modello supporta una versione minima specifica (e versioni successive, se presenti) del .NET Framework. Se si specifica l' `RequiredFrameworkVersion` elemento e il modello non supporta una versione minima specifica del .NET Framework, l'elenco a discesa **versione Framework di destinazione** viene visualizzato quando non è applicabile.

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

In questo esempio la versione minima del .NET Framework richiesta dal modello, rappresentata da `RequiredFrameworkVersion` , è 3,0. Un progetto creato con questo modello può avere come destinazione .NET Framework versioni a partire da 3,0.

## <a name="see-also"></a>Vedi anche

- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Panoramica sull'impostazione dei framework di destinazione](../ide/visual-studio-multi-targeting-overview.md)
