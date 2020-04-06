---
title: Elemento SortOrder (modelli di Visual Studio) Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699960"
---
# <a name="sortorder-element-visual-studio-templates"></a>Elemento SortOrder (modelli di Visual Studio)
Specifica un valore utilizzato per disporre il modello, tra gli altri modelli della stessa categoria, come viene visualizzato nella finestra di dialogo **Nuovo progetto** o Aggiungi **nuovo elemento.**

 \<VSTemplate \<> TemplateData> \<SortOrder>

## <a name="syntax"></a>Sintassi

```
<SortOrder> ... </SortOrder>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Oggetto `integer` che rappresenta il valore di ordinamento.

## <a name="remarks"></a>Osservazioni
 `SortOrder` è un elemento facoltativo. Il valore predefinito è 100 e tutti i valori devono essere multipli di 10.The default value is 100, and all values must be multiples of 10.

 L'elemento `SortOrder` viene ignorato per i modelli creati dall'utente. Tutti i modelli creati dall'utente sono ordinati alfabeticamente.

 I modelli con valori di ordinamento bassi vengono visualizzati nella finestra di dialogo **Nuovo progetto** o **Nuovo elemento** prima dei modelli con valori di ordinamento elevati.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] i metadati per un modello di classe standard.

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

 In questo esempio, l'elemento `SortOrder` è relativamente alto. È probabile che [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] altri modelli `SortOrder` di elemento `290` avranno un valore inferiore a e verranno visualizzati prima di questo modello nella finestra di dialogo **Nuovo elemento.**

## <a name="see-also"></a>Vedere anche
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
