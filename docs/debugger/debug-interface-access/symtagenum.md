---
description: Specifica il tipo di simbolo.
title: SymTagEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 34a820a2387039aa502feef562e94698f920da66
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121172"
---
# <a name="symtagenum"></a>SymTagEnum
Specifica il tipo di simbolo.

## <a name="syntax"></a>Sintassi

```C++
enum SymTagEnum {
    SymTagNull,
    SymTagExe,
    SymTagCompiland,
    SymTagCompilandDetails,
    SymTagCompilandEnv,
    SymTagFunction,
    SymTagBlock,
    SymTagData,
    SymTagAnnotation,
    SymTagLabel,
    SymTagPublicSymbol,
    SymTagUDT,
    SymTagEnum,
    SymTagFunctionType,
    SymTagPointerType,
    SymTagArrayType,
    SymTagBaseType,
    SymTagTypedef,
    SymTagBaseClass,
    SymTagFriend,
    SymTagFunctionArgType,
    SymTagFuncDebugStart,
    SymTagFuncDebugEnd,
    SymTagUsingNamespace,
    SymTagVTableShape,
    SymTagVTable,
    SymTagCustom,
    SymTagThunk,
    SymTagCustomType,
    SymTagManagedType,
    SymTagDimension,
    SymTagCallSite,
    SymTagInlineSite,
    SymTagBaseInterface,
    SymTagVectorType,
    SymTagMatrixType,
    SymTagHLSLType
};
```

## <a name="elements"></a>Elementi
`SymTagNull` Indica che il simbolo non ha alcun tipo.

`SymTagExe` Indica che il simbolo è un .exe file. È presente un solo `SymTagExe` simbolo per ogni archivio simboli. Funge da ambito globale e non ha un elemento padre lessicale.

`SymTagCompiland` Indica il simbolo di compilazione per ogni componente di compilazione dell'archivio simboli. Per le applicazioni native, `SymTagCompiland` i simboli corrispondono ai file oggetto collegati all'immagine. Per alcuni tipi di immagini MSIL (Microsoft Intermediate Language), è disponibile un solo compilando per ogni classe.

`SymTagCompilandDetails` Indica che il simbolo contiene attributi estesi del compilatore. Il recupero di queste proprietà può richiedere il caricamento di simboli di compilazione.

`SymTagCompilandEnv` Indica che il simbolo è una stringa di ambiente definita per il compilazione.

`SymTagFunction` Indica che il simbolo è una funzione.

`SymTagBlock` Indica che il simbolo è un blocco annidato.

`SymTagData` Indica che il simbolo è dati.

`SymTagAnnotation` Indica che il simbolo è per un'annotazione di codice. Gli elementi figlio di questo simbolo sono stringhe di dati costanti ( `SymTagData` , `LocIsConstant` , `DataIsConstant` ). La maggior parte dei client ignora questo simbolo.

`SymTagLabel` Indica che il simbolo è un'etichetta.

`SymTagPublicSymbol` Indica che il simbolo è un simbolo pubblico. Per le applicazioni native, questo simbolo è il simbolo esterno COFF rilevato durante il collegamento dell'immagine.

`SymTagUDT` Indica che il simbolo è un tipo definito dall'utente (struttura, classe o unione).

`SymTagEnum` Indica che il simbolo è un'enumerazione.

`SymTagFunctionType` Indica che il simbolo è un tipo di firma della funzione.

`SymTagPointerType` Indica che il simbolo è un tipo puntatore.

`SymTagArrayType` Indica che il simbolo è un tipo di matrice.

`SymTagBaseType` Indica che il simbolo è un tipo di base.

`SymTagTypedef` Indica che il simbolo è un `typedef` oggetto , che è un alias per un altro tipo.

`SymTagBaseClass` Indica che il simbolo è una classe di base di un tipo definito dall'utente.

`SymTagFriend` Indica che il simbolo è un elemento friend di un tipo definito dall'utente.

`SymTagFunctionArgType` Indica che il simbolo è un argomento della funzione.

`SymTagFuncDebugStart` Indica che il simbolo è la posizione finale del codice del prologo della funzione.

`SymTagFuncDebugEnd` Indica che il simbolo è la posizione iniziale del codice dell'epilogo della funzione.

`SymTagUsingNamespace` Indica che il simbolo è un nome di spazio dei nomi, attivo nell'ambito corrente.

`SymTagVTableShape` Indica che il simbolo è una descrizione di tabella virtuale.

`SymTagVTable` Indica che il simbolo è un puntatore di tabella virtuale.

`SymTagCustom` Indica che il simbolo è un simbolo personalizzato e non viene interpretato da DIA.

`SymTagThunk` Indica che il simbolo è un thunk usato per la condivisione di dati tra codice a 16 e 32 bit.

`SymTagCustomType` Indica che il simbolo è un simbolo del compilatore personalizzato.

`SymTagManagedType` Indica che il simbolo è nei metadati.

`SymTagDimension` Indica che il simbolo è una matrice multidimensionale FORTRAN.

`SymTagCallSite` Indica che il simbolo rappresenta il sito di chiamata.

`SymTagInlineSite` Indica che il simbolo rappresenta il sito inline.

`SymTagBaseInterface` Indica che il simbolo è un'interfaccia di base.

`SymTagVectorType` Indica che il simbolo è un tipo vettore.

`SymTagMatrixType` Indica che il simbolo è un tipo matrice.

`SymTagHLSLType` Indica che il simbolo è un tipo di linguaggio shader di alto livello.

## <a name="remarks"></a>Commenti
Tutti i simboli all'interno di un file di debug hanno un tag di identificazione che specifica il tipo del simbolo.

I valori in questa enumerazione vengono restituiti da una chiamata al [metodo IDiaSymbol::get_symTag.](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)

I valori di questa enumerazione vengono passati ai metodi seguenti per limitare l'ambito della ricerca a un tipo di simbolo specifico:

- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)

- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)

- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)

- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)

- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)

- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
