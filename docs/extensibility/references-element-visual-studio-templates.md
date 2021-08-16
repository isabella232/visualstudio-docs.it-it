---
title: Elemento References (modelli Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento References e sul modo in cui raggruppa i riferimenti all'assembly aggiunti dal modello ai progetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9cf14c207d7ffb560612d963571fc11cca6d55e68ac4418afa8ec71bb69c0920
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359013"
---
# <a name="references-element-visual-studio-templates"></a>Elemento References (Visual Studio modelli)
Raggruppa i riferimenti all'assembly aggiunti dal modello ai progetti.

 \<VSTemplate> \<TemplateContent>
 \<References>

## <a name="syntax"></a>Sintassi

```xml
<References>
    <Reference>... </Reference>
    <Reference>... </Reference>
    ...
</References>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Riferimento](../extensibility/reference-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto. In un elemento devono essere `Reference` presenti uno o più `References` elementi.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Specifica il contenuto del modello.|

## <a name="remarks"></a>Commenti
 `References` è un elemento figlio facoltativo di `TemplateContent`.

 Gli elementi e possono essere usati solo nei file con estensione `Reference` `References` *vstemplate* con un `Type` valore di attributo pari a `Item` .

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato `TemplateContent` l'elemento di un modello di elemento. Questo codice XML aggiunge riferimenti agli *System.dll* *eSystem.Data.dll* assembly.

```xml
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Vedi anche
- [Visual Studio riferimento allo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto ed elemento](../ide/creating-project-and-item-templates.md)
