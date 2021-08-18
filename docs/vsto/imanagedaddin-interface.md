---
title: interfaccia IManagedAddin
description: Implementare l'interfaccia IManagedAddin per creare un componente che carica i componenti VSTO componenti aggiuntivi.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8fe3ac3ca61d54f14cd72387623461dd5057740b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147907"
---
# <a name="imanagedaddin-interface"></a>interfaccia IManagedAddin
  Implementare l'interfaccia IManagedAddin per creare un componente che carica i componenti VSTO componenti aggiuntivi. Questa interfaccia è stata aggiunta nel sistema di Microsoft Office 2007.

## <a name="syntax"></a>Sintassi

```csharp
[
    object,
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),
    pointer_default(unique),
    oleautomation
]
interface IManagedAddin : IUnknown
{
    HRESULT Load(
        [in] BSTR bstrManifestURL,
        [in] IDispatch *pdispApplication);
    HRESULT Unload();
};
```

## <a name="methods"></a>Metodi
 Nella tabella seguente sono elencati i metodi definiti dall'interfaccia IManagedAddin.

|Nome|Descrizione|
|----------|-----------------|
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Chiamato quando un'applicazione di Microsoft Office carica un componente aggiuntivo VSTO gestito.|
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Chiamato appena prima che un'applicazione di Microsoft Office scarichi un componente aggiuntivo VSTO gestito.|

## <a name="remarks"></a>Commenti
 Microsoft Office applicazioni, a partire dal sistema Microsoft Office 2007, usare l'interfaccia IManagedAddin per consentire il caricamento Office VSTO componenti aggiuntivi. È possibile implementare l'interfaccia IManagedAddin per creare il caricatore e il runtime del componente aggiuntivo VSTO per i componenti aggiuntivi VSTO gestiti, anziché usare il caricatore del componente aggiuntivo VSTO (*VSTOLoader.dll*) e [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Per altre informazioni, vedere [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

## <a name="how-managed-add-ins-are-loaded"></a>Modalità di caricamento dei componenti aggiuntivi gestiti
 All'avvio di un'applicazione vengono effettuate le operazioni seguenti:

1. L'applicazione individua i componenti aggiuntivi VSTO cercando le voci nella chiave seguente del Registro di sistema:

    **HKEY_CURRENT_USER\Software\Microsoft\Office\\ *\<application name>* \Addins\\**

    Ogni voce sotto questa chiave del Registro di sistema è un ID univoco del componente aggiuntivo VSTO. In genere, corrisponde al nome dell'assembly del componente aggiuntivo VSTO.

2. L'applicazione cerca una voce `Manifest` nella voce per ciascun componente aggiuntivo VSTO.

    I VSTO gestiti possono archiviare il percorso completo di un manifesto nella voce `Manifest` **inHKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \Addins \\ _\<add-in ID>_**. Un manifesto è un file (in genere, un file XML) che fornisce informazioni usate per consentire il caricamento del componente aggiuntivo VSTO.

3. Se l'applicazione individua una voce `Manifest` , prova a caricare un componente caricatore per componenti aggiuntivi VSTO gestiti. L'applicazione esegue questa operazione provando a creare un oggetto COM che implementa l'interfaccia IManagedAddin.

    include un componente VSTO del caricatore di componenti aggiuntivi (VSTOLoader.dll) oppure è possibile crearne uno personalizzato implementando [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] l'interfaccia ** IManagedAddin.

4. L'applicazione chiama il metodo [IManagedAddin::Load](../vsto/imanagedaddin-load.md) e passa il valore della voce `Manifest` .

5. Il metodo [IManagedAddin::Load](../vsto/imanagedaddin-load.md) esegue le attività necessarie per caricare il componente aggiuntivo VSTO, ad esempio la configurazione del dominio dell'applicazione e dei criteri di sicurezza per il componente aggiuntivo VSTO caricato.

   Per altre informazioni sulle chiavi del Registro di Microsoft Office usate dalle applicazioni per individuare e caricare componenti aggiuntivi VSTO gestiti, vedere Voci del Registro di sistema per VSTO [componenti aggiuntivi](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="guidance-to-implement-imanagedaddin"></a>Linee guida per implementare IManagedAddin
 Se si implementa IManagedAddin, è necessario registrare la DLL che contiene l'implementazione usando il CLSID seguente:

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 Microsoft Office applicazioni usano questo CLSID per creare l'oggetto COM che implementa IManagedAddin.

> [!CAUTION]
> Questo CLSID viene usato anche dal *VSTOLoader.dll* in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Pertanto, se si usa IManagedAddin per creare il caricatore del componente aggiuntivo VSTO e il componente di runtime, non è possibile distribuire il componente nei computer che eseguono componenti aggiuntivi di VSTO che si basano su [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="see-also"></a>Vedi anche
- [Informazioni di riferimento sulle API non &#40;Office sviluppo in Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
