---
title: interfaccia IManagedAddin
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b436d76164b1744cffe16593149f64d219d04bf1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541128"
---
# <a name="imanagedaddin-interface"></a>interfaccia IManagedAddin
  Implementare l'interfaccia IManagedAddin per creare un componente che carica i componenti aggiuntivi VSTO gestiti. Questa interfaccia è stata aggiunta nel sistema di Microsoft Office 2007.

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

|Name|Descrizione|
|----------|-----------------|
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Chiamato quando un'applicazione di Microsoft Office carica un componente aggiuntivo VSTO gestito.|
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Chiamato appena prima che un'applicazione di Microsoft Office scarichi un componente aggiuntivo VSTO gestito.|

## <a name="remarks"></a>Osservazioni
 Microsoft Office applicazioni, a partire dal sistema 2007 Microsoft Office, usare l'interfaccia IManagedAddin per caricare i componenti aggiuntivi VSTO di Office. È possibile implementare l'interfaccia IManagedAddin per creare il caricatore del componente aggiuntivo VSTO e il runtime per i componenti aggiuntivi VSTO gestiti, invece di usare il caricatore del componente aggiuntivo VSTO (*VSTOLoader.dll*) e [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Per altre informazioni, vedere [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

## <a name="how-managed-add-ins-are-loaded"></a>Come vengono caricati i componenti aggiuntivi gestiti
 All'avvio di un'applicazione vengono effettuate le operazioni seguenti:

1. L'applicazione individua i componenti aggiuntivi VSTO cercando le voci nella chiave seguente del Registro di sistema:

    **HKEY_CURRENT_USER \Software\Microsoft\Office \\ *\<application name>* \Addins\\**

    Ogni voce sotto questa chiave del Registro di sistema è un ID univoco del componente aggiuntivo VSTO. In genere, corrisponde al nome dell'assembly del componente aggiuntivo VSTO.

2. L'applicazione cerca una voce `Manifest` nella voce per ciascun componente aggiuntivo VSTO.

    I componenti aggiuntivi VSTO gestiti possono archiviare il percorso completo di un manifesto nella `Manifest` voce **HKEY_CURRENT_USER \software\microsoft\office \\ _\<application name>_ \Addins \\ _\<add-in ID>_ **. Un manifesto è un file (in genere, un file XML) che fornisce informazioni usate per consentire il caricamento del componente aggiuntivo VSTO.

3. Se l'applicazione individua una voce `Manifest` , prova a caricare un componente caricatore per componenti aggiuntivi VSTO gestiti. L'applicazione esegue questa operazione tentando di creare un oggetto COM che implementa l'interfaccia IManagedAddin.

    [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Include un componente caricatore del componente aggiuntivo VSTO (*VSTOLoader.dll*) oppure è possibile crearne uno personalizzato implementando l'interfaccia IManagedAddin.

4. L'applicazione chiama il metodo [IManagedAddin::Load](../vsto/imanagedaddin-load.md) e passa il valore della voce `Manifest` .

5. Il metodo [IManagedAddin::Load](../vsto/imanagedaddin-load.md) esegue le attività necessarie per caricare il componente aggiuntivo VSTO, ad esempio la configurazione del dominio dell'applicazione e dei criteri di sicurezza per il componente aggiuntivo VSTO caricato.

   Per altre informazioni sulle chiavi del registro di sistema usate dalle applicazioni Microsoft Office per individuare e caricare i componenti aggiuntivi VSTO gestiti, vedere [voci del registro di sistema per i componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="guidance-to-implement-imanagedaddin"></a>Linee guida per l'implementazione di IManagedAddin
 Se si implementa IManagedAddin, è necessario registrare la DLL che contiene l'implementazione di utilizzando il CLSID seguente:

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 Microsoft Office applicazioni utilizzano questo CLSID per creare l'oggetto COM che implementa IManagedAddin.

> [!CAUTION]
> Questo CLSID viene utilizzato anche da *VSTOLoader.dll* in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Pertanto, se si usa IManagedAddin per creare il proprio componente di runtime e caricatore del componente aggiuntivo VSTO, non è possibile distribuire il componente nei computer che eseguono componenti aggiuntivi VSTO che si basano su [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="see-also"></a>Vedere anche
- [Informazioni di riferimento sulle API non gestite &#40;sviluppo per Office in Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
