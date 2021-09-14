---
description: Espone i dettagli di un stack frame.
title: IDiaFrameData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData interface
ms.assetid: 2f1b4986-341b-4641-89a4-226e261e9d93
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 908c645931a88874f4cd4214a44d295886b4e364
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629801"
---
# <a name="idiaframedata"></a>IDiaFrameData
Espone i dettagli di un stack frame.

## <a name="syntax"></a>Sintassi

```
IDiaFrameData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
Nella tabella seguente vengono illustrati i metodi di `IDiaFrameData` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaFrameData::get_addressSection](../../debugger/debug-interface-access/idiaframedata-get-addresssection.md)|Recupera la parte di sezione dell'indirizzo del codice per il frame.|
|[IDiaFrameData::get_addressOffset](../../debugger/debug-interface-access/idiaframedata-get-addressoffset.md)|Recupera la parte offset dell'indirizzo del codice per il frame.|
|[IDiaFrameData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaframedata-get-relativevirtualaddress.md)|Recupera l'indirizzo virtuale relativo dell'immagine (RVA) del codice per il frame.|
|[IDiaFrameData::get_virtualAddress](../../debugger/debug-interface-access/idiaframedata-get-virtualaddress.md)|Recupera l'indirizzo virtuale (VA) del codice per il frame.|
|[IDiaFrameData::get_lengthBlock](../../debugger/debug-interface-access/idiaframedata-get-lengthblock.md)|Recupera la lunghezza, in byte, del blocco di codice descritto dal frame.|
|[IDiaFrameData::get_lengthLocals](../../debugger/debug-interface-access/idiaframedata-get-lengthlocals.md)|Recupera il numero di byte di variabili locali inseriti nello stack.|
|[IDiaFrameData::get_lengthParams](../../debugger/debug-interface-access/idiaframedata-get-lengthparams.md)|Recupera il numero di byte di parametri inseriti nello stack.|
|[IDiaFrameData::get_maxStack](../../debugger/debug-interface-access/idiaframedata-get-maxstack.md)|Recupera il numero massimo di byte inseriti nello stack nel frame.|
|[IDiaFrameData::get_lengthProlog](../../debugger/debug-interface-access/idiaframedata-get-lengthprolog.md)|Recupera il numero di byte di codice del prologo nel blocco .|
|[IDiaFrameData::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters.md)|Recupera il numero di byte di registri salvati inseriti nello stack.|
|[IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)|Recupera la stringa di programma utilizzata per calcolare il set di registri prima della chiamata alla funzione corrente.|
|[IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)|Recupera un flag che indica che la gestione delle eccezioni di sistema è in vigore.|
|[IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)|Recupera un flag che indica che la gestione delle eccezioni C++ è in vigore.|
|[IDiaFrameData::get_functionStart](../../debugger/debug-interface-access/idiaframedata-get-functionstart.md)|Recupera un flag che indica che il blocco contiene il punto di ingresso di una funzione.|
|[IDiaFrameData::get_allocatesBasePointer](../../debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer.md)|Recupera un flag che indica che il puntatore di base è allocato per il codice in questo intervallo di indirizzi. Questo metodo è deprecato.|
|[IDiaFrameData::get_type](../../debugger/debug-interface-access/idiaframedata-get-type.md)|Recupera il tipo di frame specifico del compilatore.|
|[IDiaFrameData::get_functionParent](../../debugger/debug-interface-access/idiaframedata-get-functionparent.md)|Recupera l'interfaccia dati del frame per la funzione di inclusione.|
|[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)|Esegue la rimozione dello stack e restituisce lo stato corrente dei registri in un'interfaccia stack walk frame.|

## <a name="remarks"></a>Commenti
 I dettagli disponibili per un frame sono relativi ai punti di esecuzione all'interno dell'intervallo di indirizzi indicato dall'indirizzo e dalla lunghezza del blocco.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Ottenere questa interfaccia chiamando i [metodi IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md) o [IDiaEnumFrameData::Item.](../../debugger/debug-interface-access/idiaenumframedata-item.md) Per informazioni [dettagliate, vedere l'interfaccia IDiaEnumFrameData.](../../debugger/debug-interface-access/idiaenumframedata.md)

## <a name="example"></a>Esempio
 In questo esempio vengono stampate le proprietà di un `IDiaFrameData` oggetto . Vedere [l'interfaccia IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) per un esempio di come viene `IDiaFrameData` ottenuta l'interfaccia.

```C++
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
Intestazione: Dia2.h

Libreria: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)
- [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)
