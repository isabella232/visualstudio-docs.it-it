---
title: Elemento Icon | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ca5ced87596b5e40ae70e3faa06e58493da3d8ab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203989"
---
# <a name="icon-element"></a>Elemento Icon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'attributo guid del tag icona è il guid di una mappa di bit definita.  L'attributo id consente di selezionare lo slot nella striscia di bitmap. Questo elemento è facoltativo.  Se questo elemento viene omesso il valore di **guidOfficeIcon:msotcidNoIcon** verrà implicita.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|GUID|Richiesto. Il guid di una mappa di bit definita.|  
|id|Richiesto. Consente di selezionare lo slot nella striscia di bitmap.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|No.|No.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|DESCRIZIONE|  
|-------------|-----------------|  
|[Elemento Buttons](../extensibility/buttons-element.md)||  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
