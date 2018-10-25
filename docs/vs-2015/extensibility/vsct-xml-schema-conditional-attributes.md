---
title: Attributi condizionali dello Schema XML VSCT | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15f3af33657bc6673f138d1223e1943308deff77
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919897"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Attributi condizionali dello schema XML VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Attributi condizionali possono essere applicati a tutti gli elementi e gli elenchi. Simboli espansione espressioni e operatori logici restituiscono true o false. Se true, l'elenco associato o elemento è incluso nell'output risultante.  
  
 Espansioni dei token può essere controllati rispetto alle altre espansioni token o costanti. La funzione Defined() viene usata per verificare se è stato definito un determinato nome, anche se non ha alcun valore.  
  
 Quando un attributo Condition è applicato a un elenco, la condizione viene applicata a ogni elemento figlio nell'elenco. Se un elemento figlio contiene un attributo Condition, quindi la condizione viene combinata con l'espressione padre mediante un'operazione con AND.  
  
 I valori 1, '1' e 'true' vengono valutati come true e 0, '0' e 'false' vengono valutate come false.  
  
## <a name="operators"></a>Operatori  
 Gli operatori seguenti possono essere utilizzati per valutare le espressioni condizionali.  
  
|Operatore|Definizione|  
|--------------|----------------|  
|(,)|Raggruppamento|  
|!|NOT logico|  
|\<, >, \<=, >=, ==, !=|Relazionale e uguaglianza|  
|e|Booleano|  
|oppure|Booleano|  
  
## <a name="examples"></a>Esempi  
  
```  
<Menu Condition="Defined(DEBUG)" …  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" …  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu …  
        </Menu>  
    </Menus>  
  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

