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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f30c6a45d4ff43811e34ec4357961e0c80ae0eb9637b9fd7aee661a54296f75f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366069"
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
|*pdispApplication*|Puntatore a un oggetto IDispatch che rappresenta l'applicazione host che sta caricando VSTO componente aggiuntivo.|

## <a name="return-value"></a>Valore restituito
 Valore HRESULT che indica se il metodo è stato completato correttamente.

## <a name="remarks"></a>Commenti
 Un manifesto è un file (in genere, un file XML) che fornisce informazioni usate per consentire il caricamento del componente aggiuntivo VSTO. Un manifesto, ad esempio, può specificare il percorso dell'assembly del componente aggiuntivo VSTO e la classe del punto di ingresso per creare un'istanza quando viene caricato il componente aggiuntivo VSTO.

 Il *parametro bstrManifestURL* contiene il valore della voce nella chiave del Registro di sistema `Manifest`HKEY_CURRENT_USER\Software\Microsoft\Office **\\ _\<application name>_ \Addins \\ _\<add-in ID>_** per il VSTO componente aggiuntivo. Per altre informazioni, vedere [Interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md).

 Implementare il metodo [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) per eseguire attività come ad esempio la configurazione del dominio dell'applicazione e dei criteri di sicurezza per il componente aggiuntivo VSTO che viene caricato.

## <a name="see-also"></a>Vedi anche
- [IManagedAddin (interfaccia)](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
