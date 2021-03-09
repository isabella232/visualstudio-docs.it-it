---
title: IManagedAddin::Load
description: Chiamato quando viene caricato un componente aggiuntivo VSTO gestito.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fc89ba13e9fc0f62b264cdb926e1a8392c0b41bd
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469762"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Chiamato quando viene caricato un componente aggiuntivo VSTO gestito.

## <a name="syntax"></a>Sintassi

```csharp
HRESULT Load([in] BSTR bstrManifestURL,
             [in] IDispatch *pdispApplication);
```

### <a name="parameters"></a>Parametri

|Parametro|Descrizione|
|---------------|-----------------|
|*bstrManifestURL*|Percorso completo del manifesto per il componente aggiuntivo VSTO.|
|*pdispApplication*|Puntatore a un IDispatch che rappresenta l'applicazione host che sta caricando il componente aggiuntivo VSTO.|

## <a name="return-value"></a>Valore restituito
 Valore HRESULT che indica se il metodo è stato completato correttamente.

## <a name="remarks"></a>Commenti
 Un manifesto è un file (in genere, un file XML) che fornisce informazioni usate per consentire il caricamento del componente aggiuntivo VSTO. Un manifesto, ad esempio, può specificare il percorso dell'assembly del componente aggiuntivo VSTO e la classe del punto di ingresso per creare un'istanza quando viene caricato il componente aggiuntivo VSTO.

 Il parametro *bstrManifestURL* contiene il valore della `Manifest` voce sotto la chiave del registro di sistema **\\ _\<application name>_ \Addins \\ _\<add-in ID>_ HKEY_CURRENT_USER\Software\Microsoft\Office** per il componente aggiuntivo VSTO. Per ulteriori informazioni, vedere [interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md).

 Implementare il metodo [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) per eseguire attività come ad esempio la configurazione del dominio dell'applicazione e dei criteri di sicurezza per il componente aggiuntivo VSTO che viene caricato.

## <a name="see-also"></a>Vedi anche
- [IManagedAddin (interfaccia)](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
