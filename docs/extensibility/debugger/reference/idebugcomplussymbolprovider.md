---
description: Rappresenta un provider di simboli COM+ con metodi specifici del codice gestito.
title: IDebugComPlusSymbolProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 524663723537dd84233a9570104a779cbc3411921640768f1bcdc6a9d89e1ee2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121308051"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Rappresenta un provider di simboli COM+ con metodi specifici del codice gestito.

## <a name="syntax"></a>Sintassi

```
IDebugComPlusSymbolProvider : IDebugSymbolProvider
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Anche se non esiste alcuna separazione tra le interfacce utili per un analizzatore di espressioni (edizione Enterprise) e quelle destinate a essere usate da un motore di debug (DE), i metodi seguenti probabilmente interesseranno solo gli sviluppatori DE: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols e UpdateSymbols.

## <a name="methods"></a>Metodi
 Oltre ai metodi [nell'interfaccia IDebugSymbolProvider,](../../../extensibility/debugger/reference/idebugsymbolprovider.md) questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Determina se i simboli di debug vengono caricati per il modulo specificato in base all'identificatore di dominio dell'applicazione.|
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Crea un tipo dal tipo primitivo specificato.|
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Mappe posizione del documento nel modulo specificato in una matrice di indirizzi di debug.|
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Recupera informazioni sul tipo sulla matrice specificata in base al relativo indirizzo di debug.|
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Recupera il nome dell'assembly in base al modulo e al dominio applicazione.|
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Recupera le classi con l'attributo specificato implementate nel linguaggio di programmazione specificato.|
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Recupera le classi con l'attributo specificato in un modulo specificato.|
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Recupera il punto di ingresso dell'applicazione.|
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Recupera l'indirizzo all'interno di una funzione che rappresenta l'offset di riga specificato.|
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Recupera il layout delle variabili locali per un set di metodi.|
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Restituisce il nome associato al token specificato in base al relativo oggetto metadati.|
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Recupera i simboli di debug con l'attributo padre specificato per il modulo specificato.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Recupera il lettore di simboli che deve essere utilizzato dal codice non gestito.|
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Recupera in un tipo di simbolo in base al relativo indirizzo di debug.|
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Determina se la funzione in corrispondenza dell'indirizzo di debug specificato viene eliminata.|
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Determina se la funzione all'indirizzo di debug specificato viene considerata non obsoleta.|
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Determina se il codice nell'indirizzo del debugger specificato è nascosto.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Carica i simboli di debug specificati in memoria.|
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Carica i simboli di debug in base al flusso di dati.|
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Sostituisce i simboli di debug correnti con quelli nel flusso di dati specificato.|
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Scarica i simboli di debug per il modulo specificato dalla memoria.|
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Aggiorna i simboli di debug in memoria con quelli del flusso di dati specificato.|

## <a name="requirements"></a>Requisiti
 Intestazione: Sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
