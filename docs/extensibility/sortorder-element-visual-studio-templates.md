---
title: Elemento SortOrder (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 935d00335a21d3e129e79ce351e554ea93787447
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699960"
---
# <a name="sortorder-element-visual-studio-templates"></a>Elemento SortOrder (modelli di Visual Studio)
Specifica un valore utilizzato per disporre il modello, tra gli altri modelli nella stessa categoria, così come viene visualizzato nella finestra di dialogo **nuovo progetto** o **Aggiungi nuovo elemento** .

 \<VSTemplate> \<TemplateData>
 \<SortOrder>

## <a name="syntax"></a>Sintassi

```
<SortOrder> ... </SortOrder>
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

 Oggetto `integer` che rappresenta il valore dell'ordinamento.

## <a name="remarks"></a>Osservazioni
 `SortOrder` è un elemento facoltativo. Il valore predefinito è 100 e tutti i valori devono essere multipli di 10.

 L' `SortOrder` elemento viene ignorato per i modelli creati dall'utente. Tutti i modelli creati dall'utente sono ordinati alfabeticamente.

 I modelli con valori di ordinamento bassi vengono visualizzati nella finestra di dialogo **nuovo progetto** o **nuovo elemento aggiunto** prima dei modelli con valori di ordinamento elevati.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modello di classe standard.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>290</SortOrder>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

 In questo esempio l' `SortOrder` elemento è relativamente elevato. È probabile che altri [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modelli di elemento abbiano un `SortOrder` valore inferiore a e che `290` verranno visualizzati prima di questo modello nella finestra di dialogo **nuovo elemento** .

## <a name="see-also"></a>Vedere anche
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
