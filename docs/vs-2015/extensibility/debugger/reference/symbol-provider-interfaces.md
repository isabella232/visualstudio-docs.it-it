---
title: Interfacce del provider di simboli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c409175fb39207bc0e83a521577ad6d641731691
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204861"
---
# <a name="symbol-provider-interfaces"></a>Interfacce del provider di simboli
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Di seguito sono riportate le interfacce di gestione dei simboli per [!INCLUDE[vsipsdk](../../../includes/vsipsdk-md.md)] .  
  
## <a name="discussion"></a>Discussione  
 Queste interfacce vengono usate per valutare le variabili in uno stack di chiamate durante la modalità di interruzioni. Sono implementate solo per i provider di simboli Common Language Runtime (SP).  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Rappresenta l'indirizzo di un elemento.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Rappresenta l'indirizzo di un elemento, fornendo l'accesso all'ID del processo.|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Rappresenta un simbolo di matrice o un tipo di matrice.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Rappresenta un simbolo di classe o un tipo di classe.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Rappresenta un provider di simboli COM+ con metodi specifici del codice gestito.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Rappresenta un provider di simboli COM+ con metodi specifici del codice gestito ed estende **IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Rappresenta un simbolo o un tipo che è un contenitore per altri simboli o tipi.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Rappresenta un attributo personalizzato che può essere associato a un simbolo.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Rappresenta una query per gli attributi personalizzati su un metodo o un tipo.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Consente di accedere agli attributi personalizzati su un simbolo.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Interfaccia di base per qualsiasi tipo che può essere determinato in fase di esecuzione.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Rappresenta un campo dinamico per un oggetto [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Rappresenta un tipo di enumerazione.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP|Estende i tipi di campi disponibili per supportare i generics di codice gestito.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Classe base per tutti i campi; rappresenta una descrizione di un simbolo o di un tipo.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Rappresenta la definizione di un campo per un tipo generico di codice gestito.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Rappresenta un'istanza di un campo per un tipo generico di codice gestito.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Rappresenta un parametro per un tipo generico di codice gestito.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Rappresenta un metodo.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Rappresenta un modificatore facoltativo di debug.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Rappresenta un puntatore.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Rappresenta un valore di enumerazione di tipo primitivo da un'interfaccia [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Rappresenta una proprietà di una classe di codice gestito che può essere Get o set.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Rappresenta un provider di simboli che fornisce i simboli e i tipi.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Rappresenta un provider di simboli con accesso diretto a metadati e interfacce di simboli di base.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Rappresenta la possibilità di creare un campo che rappresenta un tipo.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Estende **IDebugTypeFieldBuilder** per poter creare tipi di matrici.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Rappresenta una raccolta di oggetti [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Rappresenta una raccolta di oggetti [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) .|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Rappresenta una raccolta di oggetti [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
