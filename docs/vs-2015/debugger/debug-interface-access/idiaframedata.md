---
title: IDiaFrameData | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData interface
ms.assetid: 2f1b4986-341b-4641-89a4-226e261e9d93
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9619d4f3d5670d3692c21d850201a2f39d96b922
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202582"
---
# <a name="idiaframedata"></a>IDiaFrameData
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Espone i dettagli di uno stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaFrameData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaFrameData`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaFrameData::get_addressSection](../../debugger/debug-interface-access/idiaframedata-get-addresssection.md)|Recupera la parte della sezione dell'indirizzo del codice per il frame.|  
|[IDiaFrameData::get_addressOffset](../../debugger/debug-interface-access/idiaframedata-get-addressoffset.md)|Recupera la parte offset di indirizzo del codice per il frame.|  
|[IDiaFrameData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaframedata-get-relativevirtualaddress.md)|Recupera l'immagine indirizzo virtuale relativo (RVA) del codice per il frame.|  
|[IDiaFrameData::get_virtualAddress](../../debugger/debug-interface-access/idiaframedata-get-virtualaddress.md)|Recupera l'indirizzo virtuale (valutazione della vulnerabilità) del codice per il frame.|  
|[IDiaFrameData::get_lengthBlock](../../debugger/debug-interface-access/idiaframedata-get-lengthblock.md)|Recupera la lunghezza, espressa in byte, del blocco di codice descritto dal frame.|  
|[IDiaFrameData::get_lengthLocals](../../debugger/debug-interface-access/idiaframedata-get-lengthlocals.md)|Recupera il numero di byte delle variabili locali inserite nello stack.|  
|[IDiaFrameData::get_lengthParams](../../debugger/debug-interface-access/idiaframedata-get-lengthparams.md)|Recupera il numero di byte dei parametri inseriti nello stack.|  
|[IDiaFrameData::get_maxStack](../../debugger/debug-interface-access/idiaframedata-get-maxstack.md)|Recupera il numero massimo di byte inseriti nello stack nel frame.|  
|[IDiaFrameData::get_lengthProlog](../../debugger/debug-interface-access/idiaframedata-get-lengthprolog.md)|Recupera il numero di byte del codice di prologo nel blocco.|  
|[IDiaFrameData::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters.md)|Recupera il numero di byte di registra salvato inseriti nello stack.|  
|[IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)|Recupera la stringa nel programma che viene usata per calcolare il set prima della chiamata alla funzione corrente di registri.|  
|[IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)|Recupera un flag che indica che la gestione delle eccezioni di sistema è attivo.|  
|[IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)|Recupera un flag che indica che la gestione delle eccezioni C++ è attivo.|  
|[IDiaFrameData::get_functionStart](../../debugger/debug-interface-access/idiaframedata-get-functionstart.md)|Recupera un flag che indica che il blocco contiene il punto di ingresso di una funzione.|  
|[IDiaFrameData::get_allocatesBasePointer](../../debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer.md)|Recupera un flag che indica che il puntatore di base viene allocato per il codice in questo intervallo di indirizzi. Metodo deprecato.|  
|[IDiaFrameData::get_type](../../debugger/debug-interface-access/idiaframedata-get-type.md)|Recupera il tipo di frame specifici del compilatore.|  
|[IDiaFrameData::get_functionParent](../../debugger/debug-interface-access/idiaframedata-get-functionparent.md)|Recupera frame dell'interfaccia di dati per la funzione di inclusione.|  
|[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)|Esegue la rimozione dello stack e restituisce lo stato corrente dei registri in un'interfaccia di frame dello stack del percorso.|  
  
## <a name="remarks"></a>Note  
 I dettagli disponibili per un frame sono per i punti di esecuzione all'interno dell'intervallo di indirizzi indicato dalla lunghezza indirizzo e blocco.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Ottenere questa interfaccia chiamando il [Idiaenumframedata](../../debugger/debug-interface-access/idiaenumframedata-next.md) oppure [Idiaenumframedata](../../debugger/debug-interface-access/idiaenumframedata-item.md) metodi. Vedere le [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) interfaccia per i dettagli.  
  
## <a name="example"></a>Esempio  
 Questo esempio visualizza le proprietà di un `IDiaFrameData` oggetto. Vedere le [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) interfaccia per un esempio di come il `IDiaFrameData` interfaccia viene ottenuta.  
  
```cpp#  
void PrintFrameData(IDiaFrameData* pFrameData){  
    DWORD dwSect;  
    DWORD dwOffset;  
    DWORD cbBlock;  
    DWORD cbLocals; // Number of bytes reserved for the function locals  
    DWORD cbParams; // Number of bytes reserved for the function arguments  
    DWORD cbMaxStack;  
    DWORD cbProlog;  
    DWORD cbSavedRegs;  
    BOOL  bSEH;  
    BOOL  bEH;  
    BOOL  bStart;  
    BSTR  wszProgram;  
  
    if(pFrameData->get_addressSection(&dwSect) == S_OK &&   
       pFrameData->get_addressOffset(&dwOffset) == S_OK &&  
       pFrameData->get_lengthBlock(&cbBlock) == S_OK &&  
       pFrameData->get_lengthLocals(&cbLocals) == S_OK &&  
       pFrameData->get_lengthParams(&cbParams) == S_OK &&  
       pFrameData->get_maxStack(&cbMaxStack) == S_OK &&  
       pFrameData->get_lengthProlog(&cbProlog) == S_OK &&  
       pFrameData->get_lengthSavedRegisters(&cbSavedRegs) == S_OK &&  
       pFrameData->get_systemExceptionHandling(&bSEH) == S_OK &&  
       pFrameData->get_cplusplusExceptionHandling(&bEH) == S_OK &&  
       pFrameData->get_functionStart(&bStart) == S_OK )  
    {  
        wprintf(L"Frame address  : %04X:%08X\n", dwSect, dwOffset);  
        wprintf(L"Block size     : 0x%8X\n", cbBlock);  
        wprintf(L"Locals size    : 0x%8X\n", cbLocals);  
        wprintf(L"Parms size     : 0x%8X\n", cbParams);  
        wprintf(L"Max stack used : 0x%8X\n", cbMaxStack);  
        wprintf(L"Prolog size    : 0x%8X\n", cbProlog);  
        wprintf(L"Saved regs size: 0x%8X\n", cbSavedRegs);  
        wprintf(L"System Exception Handling: %c\n", bSEH ? L'Y' : L'N');  
        wprintf(L"C++ Exception Handling   : %c\n", bEH ? L'Y' : L'N');  
        wprintf(L"Function starts in block : %c\n", bStart ? L'Y' : L'N');  
  
        if (pFrameData->get_program(&wszProgram) == S_OK)  
        {  
            wprintf(L"Program used for register set: %s\n", wszProgram);  
            SysFreeString(wszProgram);  
        }  
        else  
        {  
            wprintf(L"\n");  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: DIA2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)   
 [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)
