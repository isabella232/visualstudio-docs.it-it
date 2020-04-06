---
title: Elemento RequiredFrameworkVersion (modelli di Visual Studio) Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 060ebc0633de67d93257e24c2dff24d2aa0970da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701507"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Elemento RequiredFrameworkVersion (modelli di Visual Studio)

Specifica la versione minima di .NET Framework richiesta dal modello. Fa sì che l'elenco a discesa **Versione framework** di destinazione da visualizzare nella finestra di dialogo **Nuovo progetto.** L'elemento `RequiredFrameworkVersion` determina anche il valore più basso disponibile nell'elenco a discesa.

> [!IMPORTANT]
> A partire da Visual Studio 2017 versione 15.6, l'elenco a discesa **Versione framework** di destinazione non è più un filtro per i modelli visualizzati nella sezione **Modelli** della finestra di dialogo **Nuovo progetto.** Al contrario, l'elenco a discesa funziona come una selezione framework per il modello selezionato.

 \<VSTemplate \<> TemplateData> \<RequiredFrameworkVersion>

## <a name="syntax"></a>Sintassi

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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

 Il testo deve essere il numero di versione minimo di .NET Framework necessario per il modello.

## <a name="remarks"></a>Osservazioni

`RequiredFrameworkVersion` è un elemento facoltativo. Utilizzare questo elemento solo se il modello supporta una versione minima specifica (e versioni successive, se presente) di .NET Framework. Se si `RequiredFrameworkVersion` specifica l'elemento e il modello non supporta una versione minima specifica di .NET Framework, l'elenco a discesa **Versione framework** di destinazione viene visualizzato quando non è applicabile.

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

In questo esempio, la versione minima di .NET Framework richiesta `RequiredFrameworkVersion`dal modello, rappresentata da , è 3.0. Un progetto creato con questo modello può essere destinato alle versioni di .NET Framework a partire dalla 3.0.A project created with this template can target .NET Framework versions starting from 3.0.

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Panoramica sull'impostazione dei framework di destinazione](../ide/visual-studio-multi-targeting-overview.md)
