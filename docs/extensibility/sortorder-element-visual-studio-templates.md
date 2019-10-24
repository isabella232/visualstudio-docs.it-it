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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2875bcb4583c1d2ec47a935d1a8bb4f0de109a92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719917"
---
# <a name="sortorder-element-visual-studio-templates"></a>Elemento SortOrder (modelli di Visual Studio)
Specifica un valore utilizzato per disporre il modello, tra gli altri modelli nella stessa categoria, così come viene visualizzato nella finestra di dialogo **nuovo progetto** o **Aggiungi nuovo elemento** .

 \<VSTemplate > \<TemplateData > \<SortOrder >

## <a name="syntax"></a>Sintassi

```
<SortOrder> ... </SortOrder>
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

 @No__t_0 che rappresenta il valore dell'ordinamento.

## <a name="remarks"></a>Note
 `SortOrder` è un elemento facoltativo. Il valore predefinito è 100 e tutti i valori devono essere multipli di 10.

 L'elemento `SortOrder` viene ignorato per i modelli creati dall'utente. Tutti i modelli creati dall'utente sono ordinati alfabeticamente.

 I modelli con valori di ordinamento bassi vengono visualizzati nella finestra di dialogo **nuovo progetto** o **nuovo elemento aggiunto** prima dei modelli con valori di ordinamento elevati.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per un modello di classe di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] standard.

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

 In questo esempio, l'elemento `SortOrder` è relativamente elevato. È probabile che altri modelli di elemento [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] avranno un valore `SortOrder` minore di `290` e verranno visualizzati prima di questo modello nella finestra di dialogo **nuovo elemento** .

## <a name="see-also"></a>Vedere anche
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)