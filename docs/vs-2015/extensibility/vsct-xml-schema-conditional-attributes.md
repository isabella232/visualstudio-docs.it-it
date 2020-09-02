---
title: Attributi condizionali di XML Schema VSCT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6294ee8027b61840149096561efc91b8a4a3c3ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62422159"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Attributi condizionali dello schema XML VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli attributi condizionali possono essere applicati a tutti gli elenchi e gli elementi. Gli operatori logici e le espressioni di espansione simboli restituiscono true o false. Se true, l'elenco o l'elemento associato viene incluso nell'output risultante.  
  
 Le espansioni del token possono essere testate con altre espansioni o costanti del token. La funzione definita () viene utilizzata per verificare se è stato definito un determinato nome, anche se non dispone di alcun valore.  
  
 Quando viene applicato un attributo Condition a un elenco, la condizione viene applicata a ogni elemento figlio dell'elenco. Se un elemento figlio contiene un attributo Condition, la relativa condizione viene combinata con l'espressione padre da un'operazione AND.  
  
 I valori 1,' 1' è true ' vengono valutati come true e 0,' 0' è false ' vengono valutati come false.  
  
## <a name="operators"></a>Operatori  
 Gli operatori seguenti possono essere utilizzati per valutare le espressioni condizionali.  
  
|Operatore|Definizione|  
|--------------|----------------|  
|(,)|Raggruppamento|  
|!|NOT logico|  
|\<, >, \<=, >=, ==, !=|Relazionale e uguaglianza|  
|e|Boolean|  
|oppure|Boolean|  
  
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
 [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
