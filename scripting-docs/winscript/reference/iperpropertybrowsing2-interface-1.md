---
title: IPerPropertyBrowsing2 Interface 1 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bded7159b72fc8c1ae8408611ce858105e6734da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344031"
---
# <a name="iperpropertybrowsing2-interface-1"></a>Interfaccia IPerPropertyBrowsing2 1
Gli accessi le informazioni nelle pagine delle proprietà offerte da un oggetto.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|`GetDisplayString`|Restituisce una stringa di testo che descrive la proprietà specificata.|  
|`MapPropertyToPage`|Restituisce il CLSID della pagina delle proprietà che consente la modifica della proprietà specificata.|  
|`GetPredefinedStrings`|Restituisce una matrice calcolata di stringhe (`LPOLESTR` puntatori) Elenca le descrizioni dei valori consentiti che può accettare la proprietà specificata.|  
|`SetPredefinedValue`|Imposta il valore della proprietà con il valore predefinito identificato dal token `dwCookie.`|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: dbgprop.h