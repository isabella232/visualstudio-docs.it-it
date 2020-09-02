---
title: Elemento CustomParameter (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9063a354f03b896e189566e8d84a18caf7509db8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739425"
---
# <a name="customparameter-element-visual-studio-templates"></a>Elemento CustomParameter (modelli di Visual Studio)
Contiene il nome e il valore di un parametro personalizzato da utilizzare quando un progetto o un elemento viene creato dal modello.

## <a name="syntax"></a>Sintassi

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributes

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Obbligatorio. Nome del parametro. Il formato dei parametri è $*Name*$.|
|`Value`|Obbligatorio. Valore di sostituzione per il parametro.|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Raggruppa i parametri personalizzati che devono essere passati alla creazione guidata modelli quando la procedura guidata esegue le sostituzioni dei parametri.|

## <a name="remarks"></a>Osservazioni
 Quando un modello contiene `CustomParameter` elementi, ogni istanza l' `Name` attributo viene sostituito con l' `Value` attributo nei file di progetto o di elemento creati.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato come utilizzare diversi parametri personalizzati in un modello. Quando un progetto o un elemento viene creato da un modello con i parametri personalizzati seguenti, tutte le istanze di `$color1$` e `$color2$` nei file modello verranno sostituite `Red` rispettivamente con e `Blue` .

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Vedere anche
- [Elemento CustomParameters (modelli di Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Parametri di modelli](../ide/template-parameters.md)
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
