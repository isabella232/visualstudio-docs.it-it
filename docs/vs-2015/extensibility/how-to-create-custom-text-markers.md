---
title: 'Procedura: creare marcatori di testo personalizzati | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839311"
---
# <a name="how-to-create-custom-text-markers"></a>Procedura: Creare marcatori di testo personalizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si desidera creare un marcatore di testo personalizzato per enfatizzare o organizzare il codice, è necessario eseguire la procedura seguente:  
  
- Registrare il nuovo marcatore di testo, in modo che altri strumenti possano accedervi  
  
- Fornire un'implementazione e una configurazione predefinite del marcatore di testo  
  
- Creare un servizio che può essere usato da altri processi per usare il marcatore di testo  
  
  Per informazioni dettagliate su come applicare un marcatore di testo a un'area di codice, vedere [procedura: usare gli indicatori di testo](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Per registrare un marcatore personalizzato  
  
1. Creare una voce del registro di sistema come segue:  
  
    HKEY_LOCAL_MACHINE \\ *\<Version>* marcatori Editor\External \Text \Software\Microsoft\VisualStudio\\*\<MarkerGUID>*  
  
    <em>\<MarkerGUID></em>oggetto `GUID` utilizzato per identificare il marcatore da aggiungere.  
  
    *\<Version>* è la versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ad esempio 8,0  
  
    *\<PackageGUID>* è il GUID del pacchetto VSPackage che implementa l'oggetto di automazione.  
  
   > [!NOTE]
   > Il percorso radice di HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* può essere sottoposto a override con una radice alternativa quando viene inizializzata la shell di Visual Studio. per ulteriori informazioni, vedere [Opzioni della riga di comando](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2. Creare quattro valori in HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* \Text Editor\External markers\\*\<MarkerGUID>*  
  
   - Valore predefinito.  
  
   - Servizio  
  
   - DisplayName  
  
   - Pacchetto  
  
   - `Default` è una voce facoltativa di tipo REG_SZ. Quando è impostata, il valore della voce è una stringa che contiene alcune informazioni di identificazione utili, ad esempio "marcatore di testo personalizzato".  
  
   - `Service` è una voce di tipo REG_SZ contenente la stringa GUID del servizio che fornisce il marcatore di testo personalizzato da profondendo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> . Il formato è {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
   - `DisplayName` è una voce di tipo REG_SZ contenente l'ID risorsa del nome del marcatore di testo personalizzato. Il formato è #YYYY.  
  
   - `Package` voce di tipo REG_SZ contenente l'oggetto `GUID` di VSPackage che fornisce il servizio elencato in servizio. Il formato è {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Per creare un marcatore di testo personalizzato  
  
1. Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>.  
  
     L'implementazione di questa interfaccia definisce il comportamento e l'aspetto del tipo di marcatore personalizzato.  
  
     Questa interfaccia viene chiamata quando  
  
    1. Un utente avvia l'IDE per la prima volta.  
  
    2. Un utente seleziona il pulsante **Reimposta valori predefiniti** nella pagina delle proprietà **tipi di carattere e colori** nella cartella **ambiente** , disponibile nel riquadro sinistro della finestra di dialogo **Opzioni** ottenuta dal menu **strumenti** dell'IDE.  
  
2. Implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> metodo, specificando quale `IVsPackageDefinedTextMarkerType` implementazione deve essere restituita in base al GUID del tipo di marcatore specificato nella chiamata al metodo.  
  
     L'ambiente chiama questo metodo la prima volta che viene creato il tipo di marcatore personalizzato e specifica un GUID che identifica il tipo di marcatore personalizzato.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Per dichiarare il tipo di marcatore come servizio  
  
1. Chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> metodo per <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> .  
  
     Viene restituito un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> .  
  
2. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> metodo, specificando il GUID che identifica il servizio del tipo di marcatore personalizzato e fornendo un puntatore all'implementazione dell' <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaccia. L' <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implementazione deve restituire un puntatore all'implementazione dell' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> interfaccia.  
  
     Cookie univoco che identifica il servizio restituito. Questo cookie può essere usato in un secondo momento per revocare il servizio del tipo di marcatore personalizzato chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metodo dell' <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfaccia che specifica questo valore del cookie.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di marcatori di testo con l'API legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Procedura: aggiungere marcatori di testo standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Procedura: implementare i marcatori di errore](../extensibility/how-to-implement-error-markers.md)   
 [Procedura: Usare i marcatori di testo](../extensibility/how-to-use-text-markers.md)
