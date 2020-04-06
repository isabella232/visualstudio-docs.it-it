---
title: Elemento Reference (modelli di Visual Studio) Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11d893f6268a69172d27a0f7caee707767abfe89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701618"
---
# <a name="reference-element-visual-studio-templates"></a>Elemento Reference (modelli di Visual Studio)
Specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto.

 \<VSTemplate \<> TemplateContent \< \<> riferimenti> riferimento>

## <a name="syntax"></a>Sintassi

```xml
<Reference>
    <Assembly> ... </Assembly>
</Reference>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 No.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Assemblea](../extensibility/assembly-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica le informazioni su un assembly, che il modello utilizza per aggiungere un riferimento di tale assembly ai progetti. Deve essere `Assembly` presente un `Reference` elemento in ogni elemento.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Riferimenti](../extensibility/references-element-visual-studio-templates.md)|Raggruppa l'assembly a cui il modello aggiunge ai progetti.|

## <a name="remarks"></a>Osservazioni
 `Reference` è un elemento figlio obbligatorio di `References`.

 Gli `Reference` `References` elementi e possono essere utilizzati solo `Type` nei file `Item` *.vstemplate* con un valore di attributo di .

## <a name="example"></a>Esempio
 Nell'esempio seguente `TemplateContent` viene illustrato l'elemento di un modello di elemento. Questo codice XML aggiunge riferimenti agli assembly *System.dll* e *System.Data.dll.*

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

## <a name="see-also"></a>Vedere anche
- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
