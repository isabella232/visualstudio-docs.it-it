---
title: IPerPropertyBrowsing2 Interface 1 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 156cf9a1e104b8a2d7ffe4e48bd39642ef1abbd0
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159582"
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