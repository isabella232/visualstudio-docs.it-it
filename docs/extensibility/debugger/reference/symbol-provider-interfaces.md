---
title: Interfacce del provider di simboli | Microsoft Docs
description: Questo articolo contiene collegamenti alle descrizioni per le interfacce di gestione dei simboli per Visual Studio SDK, che valutano le variabili in uno stack di chiamate durante la modalità di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 14cb7be76bc941fd04eba217f0708ae94817821034b0dd1999ce194e090105a4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389007"
---
# <a name="symbol-provider-interfaces"></a>Interfacce del provider di simboli
Di seguito sono riportate le interfacce di gestione dei simboli per [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] .

## <a name="discussion"></a>Discussione
 Queste interfacce vengono usate per valutare le variabili in uno stack di chiamate durante la modalità di interruzione. Vengono implementati solo per i provider di simboli di Common Language Runtime (SP).

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Rappresenta l'indirizzo di un elemento.|
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Rappresenta l'indirizzo di un elemento, fornendo l'accesso all'ID processo.|
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Rappresenta un simbolo di matrice o un tipo di matrice.|
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Rappresenta un simbolo di classe o un tipo di classe.|
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Rappresenta un provider di simboli COM+ con metodi specifici del codice gestito.|
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Rappresenta un provider di simboli COM+ con metodi specifici del codice gestito ed estende **IDebugComPlusSymbolProvider**.|
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Rappresenta un simbolo o un tipo che è un contenitore per altri simboli o tipi.|
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Rappresenta un attributo personalizzato che può essere associato a un simbolo.|
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Rappresenta una query per gli attributi personalizzati in un metodo o un tipo.|
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Fornisce l'accesso agli attributi personalizzati in un simbolo.|
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Interfaccia di base per qualsiasi tipo che può essere determinato in fase di esecuzione.|
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Rappresenta un campo dinamico per un [oggetto IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)|
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Rappresenta un tipo di enumerazione.|
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Sp|Estende i tipi di campi disponibili per supportare i generics di codice gestito.|
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Classe di base per tutti i campi. rappresenta una descrizione di un simbolo o di un tipo.|
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Rappresenta la definizione di un campo per un tipo generico di codice gestito.|
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Rappresenta un'istanza di un campo per un tipo generico di codice gestito.|
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Rappresenta un parametro per un tipo generico di codice gestito.|
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Rappresenta un metodo.|
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Rappresenta un modificatore facoltativo di debug.|
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Rappresenta un puntatore.|
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Rappresenta un valore di enumerazione del tipo primitivo da [un'interfaccia IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)|
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Rappresenta una proprietà di una classe di codice gestito che può essere ottiene o impostata.|
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Rappresenta un provider di simboli che fornisce simboli e tipi.|
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Rappresenta un provider di simboli con accesso diretto ai metadati e alle interfacce dei simboli di base.|
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Rappresenta la possibilità di creare un campo che rappresenta un tipo.|
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Estende **IDebugTypeFieldBuilder** per poter creare tipi di matrice.|
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Rappresenta una raccolta di [oggetti IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)|
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Rappresenta una raccolta di [oggetti IDebugCustomAttribute.](../../../extensibility/debugger/reference/idebugcustomattribute.md)|
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Rappresenta una raccolta di [oggetti IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)|

## <a name="see-also"></a>Vedi anche
- [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
