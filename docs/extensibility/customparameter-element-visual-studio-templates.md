---
title: Elemento CustomParameter (modelli di Visual Studio) . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739425"
---
# <a name="customparameter-element-visual-studio-templates"></a>Elemento CustomParameter (modelli di Visual Studio)
Contiene un nome e un valore di parametro personalizzati da utilizzare quando viene creato un progetto o un elemento dal modello.

## <a name="syntax"></a>Sintassi

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Obbligatorio. Nome del parametro. Il formato per i parametri è*il nome.*|
|`Value`|Obbligatorio. Valore di sostituzione per il parametro.|

### <a name="child-elements"></a>Elementi figlio
 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Raggruppa i parametri personalizzati che devono essere passati alla creazione guidata modello quando la procedura guidata effettua sostituzioni di parametri.|

## <a name="remarks"></a>Osservazioni
 Quando un `CustomParameter` modello contiene elementi, ogni istanza dell'attributo `Name` viene sostituita con l'attributo `Value` nei file di progetto o di elemento creati.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato come utilizzare diversi parametri personalizzati in un modello. Quando un progetto o un elemento viene creato da un `$color1$` `$color2$` modello con i seguenti `Red` parametri `Blue`personalizzati, tutte le istanze di e nei file di modello verranno sostituite rispettivamente con e , .

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Vedere anche
- [Elemento CustomParameters (modelli di Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Parametri di modelli](../ide/template-parameters.md)
- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
