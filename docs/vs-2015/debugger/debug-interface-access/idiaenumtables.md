---
title: IDiaEnumTables | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables interface
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 184dadaeecad85f93afc92795e081e9bd9fb06e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696966"
---
# <a name="idiaenumtables"></a>IDiaEnumTables
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Enumera le varie tabelle contenute nell'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaEnumTables : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IDiaEnumTables` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaEnumTables::get__NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|Recupera la versione dell' [interfaccia IEnumVARIANT](https://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e) dell'enumeratore.|  
|[IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|Recupera il numero di tabelle.|  
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Recupera una tabella per mezzo di un indice o un nome.|  
|[IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)|Recupera un numero specificato di tabelle nella sequenza di enumerazione.|  
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Ignora un numero specificato di tabelle in una sequenza di enumerazione.|  
|[IDiaEnumTables::Reset](../../debugger/debug-interface-access/idiaenumtables-reset.md)|Riporta all'inizio la sequenza di enumerazione.|  
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Ottenere questa interfaccia chiamando il metodo [IDiaSession:: getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) .  
  
## <a name="example"></a>Esempio  
 Questo esempio illustra come ottenere l' `IDiaEnumTables` interfaccia da una sessione. Per un esempio più completo dell'utilizzo delle tabelle, vedere l'interfaccia [IDiaTable](../../debugger/debug-interface-access/idiatable.md) .  
  
```cpp#  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    // Do something with table  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: dia2. h  
  
 Libreria: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
