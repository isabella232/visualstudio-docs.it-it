---
title: SymTagEnum | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a9b3f28858bdeb6783175301de40de0d492739a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875217"
---
# <a name="symtagenum"></a>SymTagEnum
Specifica il tipo del simbolo.  
  
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
 `SymTagNull`  
 Indica che il simbolo non dispone di alcun tipo.  
  
 `SymTagExe`  
 Indica che il simbolo è un file .exe. È presente un solo `SymTagExe` simbolo per ogni archivio dei simboli. Viene usata come ambito globale e non ha un padre lessicale.  
  
 `SymTagCompiland`  
 Indica il simbolo di compilando per ciascun componente compilando dell'archivio simboli. Per le applicazioni native, `SymTagCompiland` simboli corrispondano per i file oggetto collegati nell'immagine. Per alcuni tipi di immagini di Microsoft Intermediate Language (MSIL), è disponibile un modulo per ogni classe.  
  
 `SymTagCompilandDetails`  
 Indica che il simbolo contiene gli attributi estesi del modulo diversamente. Recupero di queste proprietà può richiedere il caricamento dei simboli compilando.  
  
 `SymTagCompilandEnv`  
 Indica che il simbolo è una stringa di ambiente definita per il modulo.  
  
 `SymTagFunction`  
 Indica che il simbolo è una funzione.  
  
 `SymTagBlock`  
 Indica che il simbolo è un blocco nidificato.  
  
 `SymTagData`  
 Indica che il simbolo dei dati.  
  
 `SymTagAnnotation`  
 Indica che il simbolo è per un'annotazione del codice. Gli elementi figlio di questo simbolo sono stringhe di dati costanti (`SymTagData`, `LocIsConstant`, `DataIsConstant`). La maggior parte dei client ignora questo simbolo.  
  
 `SymTagLabel`  
 Indica che il simbolo è un'etichetta.  
  
 `SymTagPublicSymbol`  
 Indica che il simbolo è un simbolo pubblico. Per le applicazioni native, questo simbolo è il simbolo esterno COFF rilevato durante il collegamento dell'immagine.  
  
 `SymTagUDT`  
 Indica che il simbolo è un tipo definito dall'utente (struttura, classe o un'unione).  
  
 `SymTagEnum`  
 Indica che il simbolo è un'enumerazione.  
  
 `SymTagFunctionType`  
 Indica che il simbolo è un tipo di firma della funzione.  
  
 `SymTagPointerType`  
 Indica che il simbolo è un tipo di puntatore.  
  
 `SymTagArrayType`  
 Indica che il simbolo è un tipo di matrice.  
  
 `SymTagBaseType`  
 Indica che il simbolo è un tipo di base.  
  
 `SymTagTypedef`  
 Indica che il simbolo è un `typedef`, vale a dire, un alias per un altro tipo.  
  
 `SymTagBaseClass`  
 Indica che il simbolo è una classe di base di un tipo definito dall'utente.  
  
 `SymTagFriend`  
 Indica che il simbolo è un elemento friend di un tipo definito dall'utente.  
  
 `SymTagFunctionArgType`  
 Indica che il simbolo è un argomento di funzione.  
  
 `SymTagFuncDebugStart`  
 Indica che il simbolo è la posizione finale del codice di prologo della funzione.  
  
 `SymTagFuncDebugEnd`  
 Indica che il simbolo è la posizione iniziale del codice di epilogo della funzione.  
  
 `SymTagUsingNamespace`  
 Indica che il simbolo è un nome, lo spazio dei nomi attivo nell'ambito corrente.  
  
 `SymTagVTableShape`  
 Indica che il simbolo è una descrizione della tabella virtuale.  
  
 `SymTagVTable`  
 Indica che il simbolo è un puntatore alla tabella virtuale.  
  
 `SymTagCustom`  
 Indica che il simbolo è un simbolo personalizzato e non viene interpretato dal DIA.  
  
 `SymTagThunk`  
 Indica che il simbolo è un thunk utilizzato per la condivisione dei dati tra 16 e il codice a 32 bit.  
  
 `SymTagCustomType`  
 Indica che il simbolo è un simbolo di compilatori personalizzati.  
  
 `SymTagManagedType`  
 Indica che il simbolo è nei metadati.  
  
 `SymTagDimension`  
 Indica che il simbolo è una matrice multidimensionale di FORTRAN.  
  
 `SymTagCallSite`  
 Indica che il simbolo rappresenta il sito di chiamata.  
  
 `SymTagInlineSite`  
 Indica che il simbolo rappresenta il sito inline.  
  
 `SymTagBaseInterface`  
 Indica che il simbolo è un'interfaccia di base.  
  
 `SymTagVectorType`  
 Indica che il simbolo è un tipo di vettore.  
  
 `SymTagMatrixType`  
 Indica che il simbolo è un tipo di matrice.  
  
 `SymTagHLSLType`  
 Indica che il simbolo è un tipo High Level Shader Language.  
  
## <a name="remarks"></a>Note  
 Tutti i simboli all'interno di un file di debug hanno un tag di identificazione che specifica il tipo del simbolo.  
  
 I valori di questa enumerazione vengono restituiti da una chiamata per il [Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) (metodo).  
  
 I valori di questa enumerazione vengono passati ai metodi seguenti per limitare l'ambito della ricerca a un tipo di simbolo specifico:  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Findsymbolbyaddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [Findsymbolbyrva](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [Findsymbolbyrvaex](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [Findsymbolbytoken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [Findsymbolbyva](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [Findsymbolbyvaex](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)