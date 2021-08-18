---
title: Elemento Reference (Visual Studio Templates) | Microsoft Docs
description: Informazioni sull'elemento Reference e su come specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 84aed9d443e38e6d61069f919de115394d5f8450d56b0da930d95c1a915c08e1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121336688"
---
# <a name="reference-element-visual-studio-templates"></a>Elemento Reference (Visual Studio modelli)
Specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto.

 \<VSTemplate> \<TemplateContent>
 \<References>
 \<Reference>

## <a name="syntax"></a>Sintassi

```xml
<Reference>
    <Assembly> ... </Assembly>
</Reference>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Assembly](../extensibility/assembly-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica informazioni su un assembly, che il modello usa per aggiungere un riferimento di tale assembly ai progetti. Deve essere presente un `Assembly` elemento in ogni `Reference` elemento.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Riferimenti](../extensibility/references-element-visual-studio-templates.md)|Raggruppa i riferimenti all'assembly aggiunti dal modello ai progetti.|

## <a name="remarks"></a>Commenti
 `Reference` è un elemento figlio obbligatorio di `References`.

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
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
