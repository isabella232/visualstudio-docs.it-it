---
title: Elemento padre | Microsoft Docs
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
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 12dd551380fb8e13bc54bfaac7b5c5d59bc6372d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276902"
---
# <a name="parent-element"></a>Elemento padre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'elemento padre di una pulsante o una casella combinata può essere solo un gruppo. L'elemento padre di un menu o un gruppo può essere qualsiasi altro menu o gruppo. In un [elemento CommandPlacement](../extensibility/commandplacement-element.md), questo elemento è obbligatorio; in tutte le altre istanze è facoltativo. Se questo elemento viene omesso, l'elemento padre di `Group_Undefined:0` verrà implicita.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. Identificatore di comando di GUID/ID GUID.|  
|ID|Obbligatorio. Identificatore di comando di ID di/ID GUID.|  
  
### <a name="child-elements"></a>Elementi figlio  
 nessuno  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi che un pacchetto VSPackage fornisce all'ambiente di sviluppo integrato (IDE). Ad esempio, le voci di menu, menu, barre degli strumenti e caselle combinate.|  
|[Elemento Buttons](../extensibility/buttons-element.md)|I gruppi [elemento pulsante](../extensibility/button-element.md) elementi.|  
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu che implementa un pacchetto VSPackage.|  
|[Elemento Groups](../extensibility/groups-element.md)|Contiene le voci che definiscono i gruppi di comandi di un pacchetto VSPackage.|  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

