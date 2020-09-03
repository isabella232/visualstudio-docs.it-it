---
title: Elemento padre | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2086473bc484fed4e8e351f0c3838074557586c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194084"
---
# <a name="parent-element"></a>Elemento padre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'elemento padre di un pulsante o di una casella combinata può essere solo un gruppo. L'elemento padre di un menu o di un gruppo può essere qualsiasi altro menu o gruppo. In un [elemento CommandPlacement](../extensibility/commandplacement-element.md), questo elemento è obbligatorio. in tutti gli altri casi è facoltativa. Se questo elemento viene omesso, l'elemento padre di `Group_Undefined:0` sarà implicito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. GUID dell'identificatore del comando GUID/ID.|  
|id|Obbligatorio. ID dell'identificatore del comando GUID/ID.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi forniti da un VSPackage all'Integrated Development Environment (IDE). Ad esempio, le voci di menu, i menu, le barre degli strumenti e le caselle combinate.|  
|[Elemento Buttons](../extensibility/buttons-element.md)|Raggruppa gli elementi [elemento del pulsante](../extensibility/button-element.md) .|  
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu implementati da un VSPackage.|  
|[Elemento groups](../extensibility/groups-element.md)|Contiene le voci che definiscono i gruppi di comandi di un VSPackage.|  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
