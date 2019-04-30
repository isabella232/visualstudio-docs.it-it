---
title: 'Procedura: Creare i marcatori di testo personalizzato | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac681879e0f7ad0902358be23d74d57ccee406f8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435975"
---
# <a name="how-to-create-custom-text-markers"></a>Procedura: Creare i marcatori di testo personalizzato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si desidera creare un marcatore di testo personalizzato per enfatizzare o organizzare il codice, è necessario eseguire i passaggi seguenti:  
  
- Registrare il marcatore di testo nuovo, in modo che altri strumenti di relativi diritti di accesso  
  
- Fornire un'implementazione predefinita e la configurazione del marcatore di testo  
  
- Creare un servizio che può essere utilizzato da altri processi per rendere utilizzare del marcatore di testo  
  
  Per informazioni dettagliate su come applicare un marcatore di testo a un'area di codice, vedere [come: Usare marcatori di testo](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Per registrare un marcatore personalizzato  
  
1. Creare una voce del Registro di sistema come indicato di seguito:  
  
    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version>* \Text Editor\External Markers\\*\<MarkerGUID>*  
  
    <em>\<MarkerGUID ></em>è un `GUID` utilizzato per identificare il marcatore da aggiungere  
  
    *\<Versione >* è la versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ad esempio 8.0  
  
    *\<PackageGUID >* è il GUID del pacchetto VSPackage che implementa l'oggetto di automazione.  
  
   > [!NOTE]
   > Il percorso radice di HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versione >* può essere sottoposto a override da un'altra radice quando viene inizializzata la shell di Visual Studio, per altre informazioni, vedere [Opzioni della riga di comando](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2. Creare quattro valori in HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versione >* \Text Editor\External marcatori\\*\<MarkerGUID >*  
  
   - (Predefinito)  
  
   - Service  
  
   - DisplayName  
  
   - Pacchetto  
  
   - `Default` è una voce facoltativa di tipo REG_SZ. Se impostato, il valore della voce è una stringa che contiene alcune utili informazioni di identificazione, ad esempio "Custom marcatore di testo".  
  
   - `Service` è una voce di tipo REG_SZ contenente la stringa del GUID del servizio che fornisce il marcatore di testo personalizzato tramite proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. Il formato è {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
   - `DisplayName` è una voce di tipo REG_SZ contenente l'ID risorsa del nome del marcatore di testo personalizzato. Il formato è #YYYY.  
  
   - `Package` voce di tipo REG_SZ contenente il `GUID` di VSPackage che fornisce il servizio elencato nel servizio. Il formato è {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Per creare un marcatore di testo personalizzato  
  
1. Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>.  
  
     L'implementazione di questa interfaccia definisce il comportamento e l'aspetto del tipo di marcatore personalizzato.  
  
     Questa interfaccia viene chiamata quando  
  
    1. Un utente avvia l'IDE per la prima volta.  
  
    2. Un utente seleziona il **Reimposta valori predefiniti** pulsante sotto il **Fonts and Colors** pagina delle proprietà nel **ambiente** cartella, nel riquadro sinistro della finestra il  **Le opzioni** finestra di dialogo ottenuto dal **strumenti** menu dell'IDE.  
  
2. Implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> metodo, specificando che `IVsPackageDefinedTextMarkerType` implementazione deve da restituire in base al tipo di marcatore GUID specificato nella chiamata al metodo.  
  
     L'ambiente chiama questa volta il primo metodo viene creato il tipo di marcatore personalizzato e specifica un GUID che identifica il tipo di marcatore personalizzato.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Dichiarare il tipo di marcatore come servizio  
  
1. Chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> metodo per <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> viene restituito.  
  
2. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> che specifica il GUID che identifica il servizio di tipo di marcatore personalizzato e specifica un puntatore all'implementazione del metodo di <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaccia. I <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implementazione deve restituire un puntatore all'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> interfaccia.  
  
     Un cookie univoco che identifica il servizio viene restituito. È possibile utilizzare questo cookie in un secondo momento per revocare il servizio di tipo di marcatori personalizzati chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metodo del <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfaccia se si specifica questo valore di cookie.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di marcatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Procedura: Aggiungere i marcatori di testo Standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Procedura: Implementare i marcatori di errore](../extensibility/how-to-implement-error-markers.md)   
 [Procedura: usare i marcatori di testo](../extensibility/how-to-use-text-markers.md)
