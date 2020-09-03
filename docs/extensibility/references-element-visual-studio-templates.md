---
title: Elemento References (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef31c5e7550ec7c6e4570d156d364afcf4ad6819
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701608"
---
# <a name="references-element-visual-studio-templates"></a>Elemento References (modelli di Visual Studio)
Raggruppa i riferimenti agli assembly aggiunti dal modello ai progetti.

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
|[Riferimento](../extensibility/reference-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto. Devono essere presenti uno o più `Reference` elementi in un `References` elemento.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Specifica il contenuto del modello.|

## <a name="remarks"></a>Osservazioni
 `References` è un elemento figlio facoltativo di `TemplateContent`.

 Gli `Reference` `References` elementi e possono essere utilizzati solo nei file con *estensione vstemplate* il cui `Type` valore di attributo è `Item` .

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato l' `TemplateContent` elemento di un modello di elemento. Il codice XML aggiunge riferimenti agli assembly *System.dll* e *System.Data.dll* .

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
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
