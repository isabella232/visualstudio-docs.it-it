---
title: Elemento Assembly (modelli di Visual Studio) . Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c80044657b16448ba4567fff839274226985fa14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740040"
---
# <a name="assembly-element-visual-studio-templates"></a>Elemento Assembly (modelli di Visual Studio)
Specifica le informazioni su un assembly, che il modello utilizza per aggiungere un riferimento di tale assembly ai progetti.

 \<VSTemplate \<> TemplateContent \< \<> \<riferimenti> riferimento> assembly>

## <a name="syntax"></a>Sintassi

```
<Assembly> AssemblyName </Assembly>
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
|[Riferimento](../extensibility/reference-element-visual-studio-templates.md)|Specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Questo testo specifica l'assembly da aggiungere a un progetto quando viene creata un'istanza del modello di elemento. Il nome dell'assembly deve essere specificato in uno dei seguenti modi:

- Come nome completo dell'assembly. Ad esempio:

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- Come semplice riferimento di testo. Ad esempio:

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Osservazioni
 `Assembly` è un elemento figlio obbligatorio di `Reference`.

 Gli `Reference` `References,` elementi `Assembly` e possono essere utilizzati solo nei `Type` file `Item` *.vstemplate* con un valore di attributo di .

## <a name="example"></a>Esempio
 Nell'esempio seguente `TemplateContent` viene illustrato l'elemento di un modello di elemento. Questo codice XML aggiunge riferimenti agli assembly *System.dll* e *System.Data.dll.*

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

## <a name="see-also"></a>Vedere anche
- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
