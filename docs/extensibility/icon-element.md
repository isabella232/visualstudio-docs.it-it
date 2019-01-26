---
title: Elemento Icon | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad2a273f533136fa75b0b064f2328b5b59d6d161
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974526"
---
# <a name="icon-element"></a>Elemento Icon
L'attributo guid del tag icona è il guid di una mappa di bit definita. Il `id` attributo consente di selezionare lo slot nella striscia di bitmap. Questo elemento è facoltativo. Se questo elemento non è incluso il valore di **guidOfficeIcon:msotcidNoIcon** verrà implicita.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. Il guid di una mappa di bit definita.|  
|ID|Obbligatorio. Consente di selezionare lo slot nella striscia di bitmap.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Nessuno.|Nessuno.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Buttons](../extensibility/buttons-element.md)||  
  
## <a name="see-also"></a>Vedere anche  
 [File di Visual Studio comando table (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)