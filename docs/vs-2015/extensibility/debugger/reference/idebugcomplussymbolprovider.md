---
title: IDebugComPlusSymbolProvider | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b70701aa9c4b339749554601e2a565c17697c6a4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967066"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Rappresenta un provider di simboli COM+ con metodi specifici di codice gestito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Anche se non vi è alcuna separazione tra le interfacce che sono utili per un analizzatore di espressioni (EE) e quelli che devono essere utilizzati da un motore di debug (DE), i metodi seguenti probabilmente più interessante per gli sviluppatori di DE solo: AreSymbolsLoaded GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols e UpdateSymbols.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi nel [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interfaccia, questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Determina se vengono caricati i simboli di debug per il modulo specificato dato l'identificatore del dominio applicazione.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Crea un tipo dal tipo primitivo specificato.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Esegue il mapping di una posizione del documento nel modulo specificato in una matrice di indirizzi di debug.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Recupera specificare le informazioni nella matrice specificata, data il relativo indirizzo di debug.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Recupera il nome dell'assembly dato il modulo e un dominio applicazione.|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Recupera le classi con l'attributo specificato vengono implementate nel linguaggio di programmazione specificato.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Recupera le classi con l'attributo specificato in un modulo specificato.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Recupera il punto di ingresso dell'applicazione.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Recupera l'indirizzo all'interno di una funzione che rappresenta l'offset di riga specificata.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Recupera il layout delle variabili locali per un set di metodi.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Restituisce il nome associato al token specificato relativo oggetto di metadati specificato.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Recupera i simboli di debug con l'attributo padre specificato per il modulo specificato.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Recupera il lettore di simboli da utilizzare dal codice non gestito.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Recupera in un tipo di simbolo dato il relativo indirizzo di debug.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Determina se la funzione in corrispondenza dell'indirizzo di debug specificata viene eliminata.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Determina se la funzione in corrispondenza dell'indirizzo di debug specificata viene considerata non aggiornata.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Determina se il codice in corrispondenza dell'indirizzo di debugger specificato è nascosto.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Carica i simboli di debug specificata in memoria.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Carica i simboli del flusso di dati di debug.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Sostituisce i simboli di debug corrente con quelli del flusso di dati specificato.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Scarica i simboli di debug per il modulo specificato dalla memoria.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Aggiorna i simboli di debug in memoria con quelli il flusso di dati specificato.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
