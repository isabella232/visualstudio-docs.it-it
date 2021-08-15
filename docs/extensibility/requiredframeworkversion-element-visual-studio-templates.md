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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5164202c10008112b6072b1a45aed7d52c3ddf0598c97f6b69b32ba1cb9aadf4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305191"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Elemento RequiredFrameworkVersion (Visual Studio modelli)

Specifica la versione minima del .NET Framework richiesta dal modello. Determina la visualizzazione **dell'elenco** a discesa Versione framework di destinazione nella finestra **di dialogo Project** configurazione. `RequiredFrameworkVersion`L'elemento determina anche il valore più basso disponibile nell'elenco a discesa.

> [!IMPORTANT]
> A partire da Visual Studio 2017 versione 15.6, l'elenco a discesa Versione **framework** di destinazione non è più un filtro per i modelli visualizzati nella sezione Modelli della finestra di dialogo Nuovo **Project.**  L'elenco a discesa funziona invece come selezione framework per il modello selezionato.

 \<VSTemplate> \<TemplateData>
 \<RequiredFrameworkVersion>

## <a name="syntax"></a>Sintassi

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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

 Il testo deve essere il numero di versione minimo .NET Framework necessario per il modello.

## <a name="remarks"></a>Commenti

`RequiredFrameworkVersion` è un elemento facoltativo. Usare questo elemento solo se il modello supporta una versione minima specifica (e versioni successive se presenti) del .NET Framework. Se si specifica l'elemento e il modello non supporta una versione minima specifica del .NET Framework, l'elenco a discesa Versione framework di destinazione viene visualizzato quando non `RequiredFrameworkVersion` è applicabile. 

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

In questo esempio la versione minima del .NET Framework richiesta dal modello, rappresentata da `RequiredFrameworkVersion` , è 3.0. Un progetto creato con questo modello può essere .NET Framework versioni precedenti a partire dalla 3.0.

## <a name="see-also"></a>Vedi anche

- [Visual Studio riferimento allo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Panoramica sull'impostazione dei framework di destinazione](../ide/visual-studio-multi-targeting-overview.md)
