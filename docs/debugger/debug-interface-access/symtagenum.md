---
title: SymTagEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 806fe878468baa06b52a15879ceaff1b376461e9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738509"
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
`SymTagNull` indica che il simbolo non è di tipo.

`SymTagExe` indica che il simbolo è un file con estensione exe. È presente un solo simbolo `SymTagExe` per archivio simboli. Funge da ambito globale e non dispone di un elemento padre lessicale.

`SymTagCompiland` indica il simbolo modulo per ogni componente modulo dell'archivio simboli. Per le applicazioni native, `SymTagCompiland` simboli corrispondono ai file oggetto collegati all'immagine. Per alcuni tipi di immagini Microsoft Intermediate Language (MSIL), esiste un modulo per ogni classe.

`SymTagCompilandDetails` indica che il simbolo contiene attributi estesi di modulo. Il recupero di queste proprietà potrebbe richiedere il caricamento di simboli modulo.

`SymTagCompilandEnv` indica che il simbolo è una stringa di ambiente definita per modulo.

`SymTagFunction` indica che il simbolo è una funzione.

`SymTagBlock` indica che il simbolo è un blocco annidato.

`SymTagData` indica che il simbolo è dati.

`SymTagAnnotation` indica che il simbolo è relativo a un'annotazione di codice. Gli elementi figlio di questo simbolo sono stringhe di dati costanti (`SymTagData`, `LocIsConstant`, `DataIsConstant`). La maggior parte dei client ignora questo simbolo.

`SymTagLabel` indica che il simbolo è un'etichetta.

`SymTagPublicSymbol` indica che il simbolo è un simbolo pubblico. Per le applicazioni native, questo simbolo è il simbolo esterno COFF rilevato durante il collegamento dell'immagine.

`SymTagUDT` indica che il simbolo è un tipo definito dall'utente (struttura, classe o Unione).

`SymTagEnum` indica che il simbolo è un'enumerazione.

`SymTagFunctionType` indica che il simbolo è un tipo di firma della funzione.

`SymTagPointerType` indica che il simbolo è un tipo di puntatore.

`SymTagArrayType` indica che il simbolo è un tipo di matrice.

`SymTagBaseType` indica che il simbolo è un tipo di base.

`SymTagTypedef` indica che il simbolo è un `typedef`, ovvero un alias per un altro tipo.

`SymTagBaseClass` indica che il simbolo è una classe di base di un tipo definito dall'utente.

`SymTagFriend` indica che il simbolo è un elemento Friend di un tipo definito dall'utente.

`SymTagFunctionArgType` indica che il simbolo è un argomento della funzione.

`SymTagFuncDebugStart` indica che il simbolo è la posizione finale del codice di prologo della funzione.

`SymTagFuncDebugEnd` indica che il simbolo è la posizione iniziale del codice dell'epilogo della funzione.

`SymTagUsingNamespace` indica che il simbolo è un nome di spazio dei nomi, attivo nell'ambito corrente.

`SymTagVTableShape` indica che il simbolo è una descrizione della tabella virtuale.

`SymTagVTable` indica che il simbolo è un puntatore a tabella virtuale.

`SymTagCustom` indica che il simbolo è un simbolo personalizzato e non è interpretato da DIA.

`SymTagThunk` indica che il simbolo è un thunk utilizzato per la condivisione di dati tra 16 e 32 di codice di bit.

`SymTagCustomType` indica che il simbolo è un simbolo del compilatore personalizzato.

`SymTagManagedType` indica che il simbolo è nei metadati.

`SymTagDimension` indica che il simbolo è una matrice multidimensionali FORTRAN.

`SymTagCallSite` indica che il simbolo rappresenta il sito di chiamata.

`SymTagInlineSite` indica che il simbolo rappresenta il sito inline.

`SymTagBaseInterface` indica che il simbolo è un'interfaccia di base.

`SymTagVectorType` indica che il simbolo è un tipo di vettore.

`SymTagMatrixType` indica che il simbolo è un tipo di matrice.

`SymTagHLSLType` indica che il simbolo è un tipo di linguaggio shader di alto livello.

## <a name="remarks"></a>Note
Tutti i simboli in un file di debug hanno un tag di identificazione che specifica il tipo del simbolo.

I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) .

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
Intestazione: cvconst. h

## <a name="see-also"></a>Vedere anche
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
