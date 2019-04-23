---
title: 'Procedura: Accedere ai tipi di carattere incorporati e combinazione di colori | Microsoft Docs'
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
ms.openlocfilehash: 496ace3193ec2a78033b2e429f6fa7c6cbf11a07
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091525"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Procedura: Accedere ai tipi di carattere incorporati e combinazione di colori
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'ambiente di sviluppo integrato (IDE) di Visual Studio è una combinazione di tipi di carattere e colori associato con la finestra dell'editor. È possibile accedere a questo schema tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia.  
  
 Per usare lo schema di colori e tipi di carattere predefiniti, un pacchetto VSPackage deve:  
  
- Definire una categoria da usare con il servizio predefinito, i tipi di carattere e colori.  
  
- Registrare la categoria con il server predefinito di tipi di carattere e colori.  
  
- Indicare all'IDE che una specifica finestra Usa gli elementi visualizzati predefiniti e le categorie mediante il `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` e `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfacce.  
  
  L'IDE Usa la categoria risulta come un handle della finestra. Nome della categoria viene visualizzato nel **Mostra impostazioni per:** casella di riepilogo a discesa nel **Fonts and Colors** pagina delle proprietà.  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Per definire una categoria utilizzando i colori e tipi di carattere predefiniti  
  
1. Creare un GUID non autorizzato.  
  
    Il GUID viene utilizzato per identificare in modo univoco una categoria<strong>.</strong> Questa categoria riutilizza specifica di colori e tipi di carattere predefiniti dell'IDE.  
  
   > [!NOTE]
   >  Durante il recupero di dati carattere e colori con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> o altre interfacce, i pacchetti VSPackage questo GUID usano per fare riferimento a informazioni incorporate.  
  
2. Nome della categoria deve essere aggiunto a una tabella di stringhe all'interno di file di risorse (RC) del pacchetto VSPackage, in modo che possa essere localizzata in base alle necessità quando visualizzati nell'IDE di.  
  
    Per altre informazioni, vedere [aggiunta o eliminazione di una stringa](http://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Per registrare una categoria utilizzando i colori e tipi di carattere predefiniti  
  
1. Costruire un tipo speciale di voce del Registro di sistema categoria nel percorso seguente:  
  
     [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio version>* \FontAndColors\\*\<Category>*]  
  
     *\<Categoria >* è il nome non localizzato della categoria.  
  
2. Popolare il Registro di sistema per usare i tipi di carattere azionari e combinazione di colori con quattro valori:  
  
    |Nome|Tipo|Dati|Descrizione|  
    |----------|----------|----------|-----------------|  
    |Category|REG_SZ|GUID|Un GUID arbitrario che identifica una categoria che contiene lo schema di carattere e colori predefinito.|  
    |Pacchetto|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Il GUID viene utilizzato da tutti i pacchetti VSPackage che utilizzano le configurazioni predefinite di carattere e colori.|  
    |NameID|REG_DWORD|Id|L'ID risorsa del nome di una categoria localizzabili nel pacchetto VSPackage.|  
    |ToolWindowPackage|REG_SZ|GUID|Il GUID della VSPackage che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia.|  
  
3. 
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Per avviare l'uso di caratteri fornita dal sistema e i colori  
  
1. Creare un'istanza di `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` interfaccia come parte dell'implementazione e l'inizializzazione della finestra.  
  
2. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodo per ottenere un'istanza del `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfaccia corrispondente all'oggetto corrente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> istanza.  
  
3. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> due volte.  
  
   - Chiamare una volta con `VSEDITPROPID_ViewGeneral_ColorCategory`come argomento.  
  
   - Chiamare una volta con `VSEDITPROPID_ViewGeneral_FontCategory` come argomento.  
  
     Questo imposta ed espone i servizi di tipi di carattere e colori predefiniti come proprietà della finestra.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente avvia l'uso di colori e tipi di carattere predefiniti.  
  
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
 [Usando tipi di carattere e colori](../extensibility/using-fonts-and-colors.md)   
 [Recuperare le informazioni di colore per la colorazione del testo e del tipo di carattere](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [L'accesso a tipo di carattere archiviata e le impostazioni dei colori](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Panoramica di tipi di carattere e colori](../extensibility/font-and-color-overview.md)
