---
title: Elemento Icon | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2494e75c312385a1a0c86709eb417d4b124a97de
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497693"
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