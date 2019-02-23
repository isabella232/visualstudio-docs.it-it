---
title: Elemento assembly (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9887214edae870ca79796a7a667b15f8536e8bb4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710981"
---
# <a name="assembly-element-visual-studio-templates"></a>Elemento assembly (modelli di Visual Studio)
Specifica le informazioni relative a un assembly, che usa il modello per aggiungere un riferimento dell'assembly per i progetti.

 \<VSTemplate > \<TemplateContent > \<riferimenti > \<riferimento > \<Assembly >

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
|[Reference](../extensibility/reference-element-visual-studio-templates.md)|Specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Questo testo specifica l'assembly da aggiungere a un progetto quando viene creata un'istanza del modello di elemento. Questo nome dell'assembly deve essere specificato in uno dei modi seguenti:

-   Come un nome completo dell'assembly. Ad esempio:

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

-   Come riferimento in testo semplice. Ad esempio:

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Note
 `Assembly` è un elemento figlio obbligatorio di `Reference`.

 Il `Reference`, `References,` e `Assembly` elementi possono essere utilizzati solo nelle *vstemplate* i file con un `Type` valore dell'attributo `Item`.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato il `TemplateContent` elemento di un modello di elemento. Questo codice XML aggiunge i riferimenti per il *System. dll* e *System* assembly.

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
- [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)