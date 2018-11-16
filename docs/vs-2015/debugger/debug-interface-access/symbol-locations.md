---
title: Percorsi dei simboli | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- LocationType values
- symbols [DIA SDK], locations
ms.assetid: 7c8cd8fe-169e-4161-9cff-5e9015984add
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54db4657ee779da1dfb5c0f743930f752ed26dbf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750553"
---
# <a name="symbol-locations"></a>Percorsi dei simboli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La maggior parte dei simboli dispongono di un percorso definito all'interno del file di immagine. Viene specificato il percorso del simbolo con un valore compreso il [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) enumerazione. Il simbolo può supportare proprietà aggiuntive in base alla relativa posizione.  
  
 La tabella seguente illustra più comunemente usati tipi di percorsi e le relative proprietà aggiuntive.  
  
|Tipo di percorso|Proprietà aggiuntive|  
|-------------------|---------------------------|  
|`LocIsNull`|none|  
|`LocIsStatic`|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)<br /><br /> [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [Get_relativevirtualaddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md) (se sono abilitati gli indirizzi virtuali relativi)<br /><br /> [Get_virtualaddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md) (se la base dell'immagine è stata impostata su diverso da zero)|  
|`LocIsTLS`|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|  
|`LocIsRegRel`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsThisRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsEnregistered`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|  
|`LocIsBitField`|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)<br /><br /> [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsSlot`|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|  
|`LocIsIlRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocInMetaData`|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|  
|`LocIsConstant`|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Get_addressoffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)   
 [Get_addresssection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [Get_bitposition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)   
 [Get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)   
 [Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)   
 [Get_registerid](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)   
 [Get_relativevirtualaddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)   
 [Get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)   
 [Get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)   
 [Get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)   
 [Get_virtualaddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)   
 [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md)   
 [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)



