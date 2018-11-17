---
title: Elemento CommandPlacements | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18c165f978ab43909d484ff13edd1d7d2ddd0f60
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782063"
---
# <a name="commandplacements-element"></a>Elemento CommandPlacements
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'elemento CommandPlacements Raggruppa gli elementi CommandPlacement e altri raggruppamenti CommandPlacements.  
  
 L'elemento CommandPlacements è facoltativo. Se nessun comandi, gruppi o i menu devono essere incluso in una posizione secondaria, non è necessario includere questa sezione nel file con estensione vsct.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<CommandPlacements>  
  <CommandPlacement>... </CommandPlacement>  
  <CommandPlacement>... </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|Condizione|Facoltativo. Visualizzare [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|CommandPlacements|Altri raggruppamenti CommandPlacements e raggruppa gli elementi CommandPlacement.|  
|[Elemento CommandPlacement](../extensibility/commandplacement-element.md)|Abilita i pulsanti, gruppi e i menu da includere in più di un gruppo o un menu.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi.|  
  
## <a name="example"></a>Esempio  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CommandPlacement](../extensibility/commandplacement-element.md)   
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

