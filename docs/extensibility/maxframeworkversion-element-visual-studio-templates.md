---
title: Elemento MaxFrameworkVersion (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a00e174e3454dcb054c13252ef699a7cbc87df8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318601"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Elemento MaxFrameworkVersion (modelli di Visual Studio)

Specifica la versione massima di .NET Framework richiesto dal modello. Determina il valore più alto disponibile nel **versione Framework di destinazione** elenco a discesa delle **nuovo progetto** finestra di dialogo. Affinché gli utenti siano in grado di selezionare una versione di framework, è necessario specificare anche [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) come la versione minima di .NET Framework per il modello.

> [!IMPORTANT]
> A partire da Visual Studio 2017 versione 15.6, il **versione Framework di destinazione** elenco a discesa non è più un filtro per i modelli visualizzati nel **modelli** sezione del **nuovo progetto** finestra di dialogo. Al contrario, il **versione Framework di destinazione** elenco a discesa funziona come un selettore di framework per il modello selezionato.

 \<VSTemplate > \<TemplateData > \<MaxFrameworkVersion >

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello e definisce come viene visualizzato in entrambi i **nuovo progetto** o il **Aggiungi nuovo elemento** nella finestra di dialogo.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo deve essere il più alto numero di versione di .NET Framework che è consentito dal modello.

## <a name="remarks"></a>Note

`MaxFrameworkVersion` è un elemento facoltativo. Il `MaxFrameworkVersion` elemento deve essere omesso solo se necessario, per non limitare inavvertitamente le versioni di intervallo supportati di .NET Framework per il modello. Deve essere omessa anche se .NET Framework non è applicabile al modello.

## <a name="example"></a>Esempio

Nell'esempio seguente vengono illustrati i metadati di un controllo standard [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modello di classe.

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

In questo esempio, la versione massima di .NET Framework richiesto dal modello, rappresentato da `MaxFrameworkVersion`, è 4.7.1. Un progetto creato con questo modello può avere come destinazione versioni di .NET Framework fino a 4.7.1.

## <a name="see-also"></a>Vedere anche

- [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
