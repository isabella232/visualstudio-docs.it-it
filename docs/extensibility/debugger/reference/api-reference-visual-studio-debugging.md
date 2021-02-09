---
title: Informazioni di riferimento sulle API (debug di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 24e7c8892798d9192aa59c946e1c978899b4d173
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912033"
---
# <a name="api-reference-visual-studio-debugging"></a>Riferimenti API (debug di Visual Studio)
La sezione di riferimento include una panoramica concettuale dell'API, una guida che mostra la sintassi e l'utilizzo di tutti gli elementi API e un assortimento di esempi di codice. Tutti i riferimenti vengono elencati in ordine alfabetico in base alla categoria.

 Nella tabella seguente vengono illustrati i `HRESULT` valori comuni restituiti dai metodi.

|Nome|Descrizione|Valore|
|----------|-----------------|-----------|
|S_OK|Esito positivo.|0x00000000|
|E_UNEXPECTED|Errore imprevisto.|0x8000FFFF|
|E_NOTIMPL|Non implementato.|0x80004001|
|E_OUTOFMEMORY|Memoria insufficiente per completare l'operazione.|0x8007000E|
|E_INVALIDARG|Uno o più argomenti non sono validi.|0x80070057|
|E_NOINTERFACE|Questa interfaccia non è supportata.|0x80004002|
|E_POINTER|Puntatore non valido.|0x80004003|
|E_HANDLE|Handle non valido.|0x80070006|
|E_ABORT|Operazione interrotta.|0x80004004|
|E_FAIL|Errore imprevisto.|0x80004005|
|E_ACCESSDENIED|Errore generale di accesso negato.|0x80070005|

> [!NOTE]
> Quando un [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] metodo di debug restituisce `S_OK` , si presuppone che tutti i puntatori di parametro out siano validi, ovvero che non venga eseguita alcuna convalida sui puntatori di parametro out quando `S_OK` viene restituito.
>
> [!NOTE]
> I parametri non validi o `NULL` [out] possono causare l'arresto anomalo dell'IDE.

## <a name="see-also"></a>Vedi anche
- [Interfacce](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Estendibilità del debugger di Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
