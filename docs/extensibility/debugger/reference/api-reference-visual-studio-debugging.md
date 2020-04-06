---
title: Guida di riferimento alle API (debug di Visual Studio) Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a2df6d82099a927664620e19096107f283afada
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738185"
---
# <a name="api-reference-visual-studio-debugging"></a>Riferimenti API (debug di Visual Studio)
La sezione di riferimento include una panoramica concettuale dell'API, una guida che mostra la sintassi e l'utilizzo per tutti gli elementi API e un assortimento di esempi di codice. Tutti i riferimenti sono elencati in ordine alfabetico per categoria.

 Nella tabella seguente `HRESULT` vengono illustrati i valori comuni restituiti dai metodi.

|Nome|Descrizione|valore|
|----------|-----------------|-----------|
|S_OK|Esito positivo.|0x00000000|
|E_UNEXPECTED|Errore imprevisto.|0x8000FFFF|
|E_NOTIMPL|Non implementato.|0x80004001|
|E_OUTOFMEMORY|Memoria insufficiente per completare l'operazione.|0x8007000E|
|E_INVALIDARG|Uno o più argomenti non sono validi.|0x80070057|
|E_NOINTERFACE|Nessuna interfaccia di questo tipo supportata.|0x80004002|
|E_POINTER|Puntatore non valido.|0x80004003|
|E_HANDLE|Handle non valido.|0x80070006|
|E_ABORT|Operazione interrotta.|0x80004004|
|E_FAIL|Errore imprevisto.|0x80004005|
|E_ACCESSDENIED|Errore generale di accesso negato.|0x80070005|

> [!NOTE]
> Quando [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] un metodo `S_OK`di debug restituisce , si presuppone che tutti i puntatori ai `S_OK` parametri out siano validi, ovvero non viene eseguita alcuna convalida sui puntatori a parametri out quando viene restituito.
>
> [!NOTE]
> Parametri `NULL` non validi o [out] possono causare l'arresto anomalo dell'IDE.

## <a name="see-also"></a>Vedere anche
- [Interfacce](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Estendibilità del debugger di Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
