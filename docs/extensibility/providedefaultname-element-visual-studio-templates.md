---
title: ProvideDefaultName (elemento) (modelli di Visual Studio) . Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 192716198f605a5f6b4f62730e84dcf83b4229cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701709"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName (elemento) (modelli di Visual Studio)
Specifica se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] il sistema del progetto genererà un nome predefinito per il modello nella finestra di dialogo **Aggiungi nuovo elemento** o Nuovo **progetto.**

 \<VSTemplate \<> TemplateData> \<provideDefaultName>

## <a name="syntax"></a>Sintassi

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
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

 Il testo deve `true` `false`essere o , che indica se generare o meno un nome predefinito per il modello nella finestra di dialogo **Aggiungi nuovo elemento** o Nuovo **progetto** .

## <a name="remarks"></a>Osservazioni
 `ProvideDefaultName` è un elemento facoltativo. Il valore predefinito è `true`.

 Se `ProvideDefaultName` `false`l'elemento è , le caselle **Nome** delle finestre `<Enter_name>`di dialogo Aggiungi nuovo **elemento** e Nuovo **progetto** contengono il valore .

 Utilizzare il [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) elemento per specificare il nome predefinito del progetto o dell'elemento nelle finestre di dialogo **Aggiungi nuovo elemento** e Nuovo **progetto** . Quando il valore `ProvideDefaultName` dell'elemento è `true` `DefaultName` , l'omissione dell'elemento per i progetti popola la finestra di dialogo con il nome del modello, ovvero il valore dell'elemento [Name](../extensibility/name-element-visual-studio-templates.md) .

## <a name="example"></a>Esempio
 Nell'esempio di `ProvideDefaultName` codice `false`riportato di seguito l'elemento viene impostato su .

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

## <a name="see-also"></a>Vedere anche
- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
