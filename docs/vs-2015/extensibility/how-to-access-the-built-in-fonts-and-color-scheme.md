---
title: 'Procedura: accedere ai tipi di carattere e alla combinazione di colori predefiniti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a43fb3a22ecb2d04542eacf07bf883590868b75b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685314"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Procedura: Accedere i tipi di carattere e alle combinazioni colori predefiniti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio Integrated Development Environment (IDE) è presente uno schema di tipi di carattere e colori associato alla finestra dell'editor. È possibile accedere a questo schema tramite l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia.  
  
 Per usare lo schema di tipi di carattere e colori predefiniti, un pacchetto VSPackage deve:  
  
- Definire una categoria da usare con il servizio colori e tipi di carattere predefiniti.  
  
- Registrare la categoria con il server dei tipi di carattere e i colori predefiniti.  
  
- Consigliare all'IDE che una finestra specifica usi gli elementi e le categorie predefiniti visualizzati usando le `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfacce e.  
  
  L'IDE usa la categoria risultante come handle per la finestra. Il nome della categoria viene visualizzato nella casella di riepilogo a discesa **Mostra impostazioni per:** della pagina delle proprietà **tipi di carattere e colori** .  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Per definire una categoria con i tipi di carattere e i colori predefiniti  
  
1. Creare un GUID arbitrario.  
  
    Questo GUID viene usato per identificare in modo univoco una categoria<strong>.</strong> Questa categoria riutilizza le specifiche predefinite dei tipi di carattere e dei colori dell'IDE.  
  
   > [!NOTE]
   > Quando si recuperano dati di tipo carattere e colore con la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> o altre interfacce, i pacchetti VSPackage usano questo GUID per fare riferimento a informazioni predefinite.  
  
2. Il nome della categoria deve essere aggiunto a una tabella di stringhe all'interno del file di risorse del pacchetto VSPackage (RC), in modo che possa essere localizzato in base alle esigenze quando viene visualizzato nell'IDE.  
  
    Per ulteriori informazioni, vedere [aggiunta o eliminazione di una stringa](https://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Per registrare una categoria con i tipi di carattere e i colori predefiniti  
  
1. Costruire un tipo speciale di voce del registro di sistema Category nel percorso seguente:  
  
     [Hklm\software\microsoft. \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<Category>* ]  
  
     *\<Category>* nome non localizzato della categoria.  
  
2. Popolare il registro di sistema per usare i tipi di carattere e la combinazione di colori predefiniti con quattro valori:  
  
    |Nome|Tipo|Dati|Descrizione|  
    |----------|----------|----------|-----------------|  
    |Category|REG_SZ|GUID|GUID arbitrario che identifica una categoria che contiene la combinazione di tipi di carattere e colori azionaria.|  
    |Pacchetto|REG_SZ|GUID|F5E7E71D-1401-11D1-883B-0000F87579D2<br /><br /> Questo GUID viene usato da tutti i pacchetti VSPackage che usano le configurazioni predefinite per il tipo di carattere e il colore.|  
    |NameID|REG_DWORD|ID|ID risorsa di un nome di categoria localizzabile nel pacchetto VSPackage.|  
    |ToolWindowPackage|REG_SZ|GUID|GUID del pacchetto VSPackage che implementa l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia.|  
  
3. 
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Per avviare l'utilizzo di tipi di carattere e colori forniti dal sistema  
  
1. Creare un'istanza dell' `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` interfaccia come parte dell'implementazione e dell'inizializzazione della finestra.  
  
2. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodo per ottenere un'istanza dell' `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfaccia corrispondente all' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> istanza corrente.  
  
3. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> due volte.  
  
   - Chiamare una sola volta con `VSEDITPROPID_ViewGeneral_ColorCategory` come argomento.  
  
   - Chiamare una sola volta con `VSEDITPROPID_ViewGeneral_FontCategory` come argomento.  
  
     Consente di impostare ed esporre i servizi di tipi di carattere e colori predefiniti come proprietà della finestra.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene avviato l'utilizzo di tipi di carattere e colori predefiniti.  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di tipi di carattere e colori](../extensibility/using-fonts-and-colors.md)   
 [Recupero delle informazioni sui colori e sui tipi di carattere per la colorazione del testo](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Accesso alle impostazioni dei tipi di carattere e dei colori archiviati](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Panoramica di tipi di carattere e colori](../extensibility/font-and-color-overview.md)
