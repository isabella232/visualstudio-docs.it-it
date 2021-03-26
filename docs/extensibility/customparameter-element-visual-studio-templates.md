---
title: Elemento CustomParameter (modelli di Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento CustomParameter e su come contiene un nome e un valore di parametro personalizzato da usare quando viene creato un progetto o un elemento dal modello.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6190dc96501221a31c9a51f59e1bd734b9e08260
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055596"
---
# <a name="customparameter-element-visual-studio-templates"></a>Elemento CustomParameter (modelli di Visual Studio)
Contiene il nome e il valore di un parametro personalizzato da utilizzare quando un progetto o un elemento viene creato dal modello.

## <a name="syntax"></a>Sintassi

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Obbligatorio. Nome del parametro. Il formato dei parametri è $*Name*$.|
|`Value`|Obbligatorio. Valore di sostituzione per il parametro.|

### <a name="child-elements"></a>Elementi figlio
 Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Raggruppa i parametri personalizzati che devono essere passati alla creazione guidata modelli quando la procedura guidata esegue le sostituzioni dei parametri.|

## <a name="remarks"></a>Commenti
 Quando un modello contiene `CustomParameter` elementi, ogni istanza l' `Name` attributo viene sostituito con l' `Value` attributo nei file di progetto o di elemento creati.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato come utilizzare diversi parametri personalizzati in un modello. Quando un progetto o un elemento viene creato da un modello con i parametri personalizzati seguenti, tutte le istanze di `$color1$` e `$color2$` nei file modello verranno sostituite `Red` rispettivamente con e `Blue` .

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Vedi anche
- [Elemento CustomParameters (modelli di Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Parametri di modelli](../ide/template-parameters.md)
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
