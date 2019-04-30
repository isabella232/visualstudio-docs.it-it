---
title: IDebugProgram2::Execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 29839e2f2adb4a0e560b5b58d4226fd61596128c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412856"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Continua l'esecuzione di questo programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente (ad esempio, un passaggio) sia deselezionata, e il programma inizia l'esecuzione anche in questo caso.

> [!NOTE]
> Metodo deprecato. Usare la [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) metodo invece.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Quando l'utente avvia l'esecuzione da uno stato di interruzione nel thread di alcuni degli altri programmi, questo metodo viene chiamato su questo programma. Questo metodo viene chiamato anche quando l'utente seleziona il **avviare** dalle **Debug** menu nell'IDE. L'implementazione di questo metodo potrebbe essere semplice come chiamare le [Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md) metodo sul thread corrente nel programma.

> [!WARNING]
> Non inviare un evento di arresto o di un evento (sincrono) immediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario, il debugger potrebbe bloccarsi.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)