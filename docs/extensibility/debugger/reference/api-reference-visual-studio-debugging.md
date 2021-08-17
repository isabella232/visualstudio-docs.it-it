---
description: La sezione di riferimento include una panoramica concettuale dell'API, una guida che illustra la sintassi e l'utilizzo di tutti gli elementi dell'API e un'ampia gamma di esempi di codice.
title: Informazioni di riferimento sulle API (Visual Studio debug) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ac51ded5f99fc2d73d09e563bdf05ee0ac40469f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073201"
---
# <a name="api-reference-visual-studio-debugging"></a>Riferimenti API (debug di Visual Studio)
La sezione di riferimento include una panoramica concettuale dell'API, una guida che illustra la sintassi e l'utilizzo di tutti gli elementi dell'API e un'ampia gamma di esempi di codice. Tutti i riferimenti sono elencati in ordine alfabetico in base alla categoria.

 La tabella seguente illustra i valori `HRESULT` comuni restituiti dai metodi.

|Nome|Descrizione|Valore|
|----------|-----------------|-----------|
|S_OK|Operazione completata.|0x00000000|
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
> Quando un metodo di debug restituisce , si presuppone che tutti i puntatori di parametro out siano validi, cio' non viene eseguita alcuna convalida sui puntatori di parametro [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] `S_OK` out quando viene `S_OK` restituito.
>
> [!NOTE]
> I parametri `NULL` non validi o [out] possono causare l'arresto anomalo dell'IDE.

## <a name="see-also"></a>Vedi anche
- [Interfacce](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Estendibilità del debugger di Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
