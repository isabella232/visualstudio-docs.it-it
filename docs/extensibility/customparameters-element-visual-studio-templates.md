---
title: Elemento CustomParameters (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f524996c226f001c68ddc7ac9aa8cb3b99857fc5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739414"
---
# <a name="customparameters-element-visual-studio-templates"></a>Elemento CustomParameters (modelli di Visual Studio)
Raggruppa i parametri personalizzati che devono essere passati alla creazione guidata modelli quando la procedura guidata esegue le sostituzioni dei parametri.

## <a name="syntax"></a>Sintassi

```
<CustomParameters>
    <CustomParameter/>
    <CustomParameter/>
</CustomParameters>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributes
 Nessuno.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Contiene il nome e il valore di un parametro personalizzato da utilizzare quando un progetto o un elemento viene creato dal modello. Possono esistere zero o più elementi `CustomParameter` in un elemento `CustomParameters`.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Specifica il contenuto del modello.|

## <a name="remarks"></a>Osservazioni

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato come utilizzare diversi parametri personalizzati in un modello. Quando un progetto o un elemento viene creato da un modello con i parametri personalizzati seguenti, tutte le istanze di `$color1$` e `$color2$` nei file modello verranno sostituite `Red` rispettivamente con e `Blue` .

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Vedere anche
- [Elemento CustomParameter (modelli di Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Parametri di modelli](../ide/template-parameters.md)
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
