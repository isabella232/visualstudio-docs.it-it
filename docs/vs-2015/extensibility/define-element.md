---
title: Definire l'elemento | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76e44ccc221b0f11f30ed63de63f82634f726b79
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526289"
---
# <a name="define-element"></a>Elemento Define
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [definire elemento](https://docs.microsoft.com/visualstudio/extensibility/define-element).  
  
Definisce una coppia nome / valore di simbolo. Questo simbolo può essere valutato da attributi condizionali. Per altre informazioni, vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md). Vedere anche il [simboli elemento](../extensibility/symbols-element.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|name|Obbligatorio. Il nome del simbolo:<br /><br /> nome = "Modalità"|  
|predefinito|Obbligatorio. Il valore del simbolo:<br /><br /> valore = "Standard"|  
|Condizione|Facoltativo. Per altre informazioni, vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi che un pacchetto VSPackage fornisce all'ambiente di sviluppo integrato (IDE). Ad esempio, le voci di menu, menu, barre degli strumenti e caselle combinate.|  
  
## <a name="example"></a>Esempio  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

