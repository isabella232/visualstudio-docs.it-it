---
title: Elemento Assembly (modelli Visual Studio) | Microsoft Docs
titleSuffix: ''
description: Informazioni sull'elemento Assembly e su come specifica le informazioni su un assembly, che il modello usa per aggiungere un riferimento di tale assembly ai progetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 54fc5cfccde99776136f0cb904d02bf6a4971045
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709821"
---
# <a name="assembly-element-visual-studio-templates"></a>Elemento Assembly (Visual Studio)
Specifica informazioni su un assembly, utilizzate dal modello per aggiungere un riferimento di tale assembly ai progetti.

 \<VSTemplate> \<TemplateContent>
 \<References>
 \<Reference>
 \<Assembly>

## <a name="syntax"></a>Sintassi

```
<Assembly> AssemblyName </Assembly>
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
|[Riferimento](../extensibility/reference-element-visual-studio-templates.md)|Specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Questo testo specifica l'assembly da aggiungere a un progetto quando viene creata un'istanza del modello di elemento. Questo nome di assembly deve essere specificato in uno dei modi seguenti:

- Come nome completo dell'assembly. Ad esempio:

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- Come riferimento di testo semplice. Ad esempio:

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Osservazioni
 `Assembly` è un elemento figlio obbligatorio di `Reference`.

 Gli elementi , e possono essere usati solo nei file con estensione `Reference` `References,` `Assembly` *vstemplate* con valore `Type` di attributo `Item` .

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato `TemplateContent` l'elemento di un modello di elemento. Questo codice XML aggiunge riferimenti agli *System.dll* e *System.Data.dll* assembly.

```
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
- [Visual Studio sullo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
