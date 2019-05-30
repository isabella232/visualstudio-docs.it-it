---
title: 'Procedura: Accedere ai tipi di carattere incorporati e combinazione di colori | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2abc6606d33e4b59faeb1838bcb173fd51a28616
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340979"
---
# <a name="how-to-access-the-built-in-fonts-and-color-ccheme"></a>Procedura: I tipi di carattere incorporati di accesso e il colore ccheme
L'ambiente di sviluppo integrato (IDE) di Visual Studio è una combinazione di tipi di carattere e colori associato con la finestra dell'editor. È possibile accedere a questo schema tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia.

 Per usare lo schema di colori e tipi di carattere predefiniti, un pacchetto VSPackage deve:

- Definire una categoria da usare con il servizio predefinito, i tipi di carattere e colori.

- Registrare la categoria con il server predefinito di tipi di carattere e colori.

- Indicare all'IDE che una specifica finestra Usa gli elementi visualizzati predefiniti e le categorie mediante il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer> interfacce.

  L'IDE Usa la categoria risulta come un handle della finestra. Nome della categoria viene visualizzato nel **Mostra impostazioni per:** casella di riepilogo a discesa nel **Fonts and Colors** pagina delle proprietà.

## <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Per definire una categoria utilizzando i colori e tipi di carattere predefiniti

1. Creare un GUID non autorizzato.

     Questo GUID è utilizzato per identificare in modo univoco una categoria. Questa categoria riutilizza specifica di colori e tipi di carattere predefiniti dell'IDE.

    > [!NOTE]
    > Durante il recupero di dati carattere e colori con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> o altre interfacce, i pacchetti VSPackage questo GUID usano per fare riferimento a informazioni incorporate.

2. Nome della categoria deve essere aggiunto a una tabella di stringhe all'interno delle risorse del pacchetto VSPackage (*RC*) del file, in modo che possa essere localizzata in base alle necessità quando visualizzati nell'IDE.

     Per altre informazioni, vedere [aggiungere o eliminare una stringa](/cpp/windows/adding-or-deleting-a-string).

### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Per registrare una categoria utilizzando i colori e tipi di carattere predefiniti

1. Costruire un tipo speciale di voce del Registro di sistema categoria nel percorso seguente:

     *[HKLM\Software\Microsoft. \Visual Studio\\\<versione di Visual Studio > \FontAndColors\\\<categoria >* ]

     *\<Categoria >* è il nome non localizzato della categoria.

2. Popolare il Registro di sistema per usare i tipi di carattere azionari e combinazione di colori con quattro valori:

    |Nome|Tipo|Dati|Descrizione|
    |----------|----------|----------|-----------------|
    |Category|REG_SZ|GUID|Un GUID arbitrario che identifica una categoria che contiene lo schema di carattere e colori predefinito.|
    |Pacchetto|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Il GUID viene utilizzato da tutti i pacchetti VSPackage che utilizzano le configurazioni predefinite di carattere e colori.|
    |NameID|REG_DWORD|Id|L'ID risorsa del nome di una categoria localizzabili nel pacchetto VSPackage.|
    |ToolWindowPackage|REG_SZ|GUID|Il GUID della VSPackage che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia.|

### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Per avviare l'uso di caratteri fornita dal sistema e i colori

1. Creare un'istanza di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaccia come parte dell'implementazione e l'inizializzazione della finestra.

2. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodo per ottenere un'istanza del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer> interfaccia corrispondente all'oggetto corrente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> istanza.

3. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> due volte.

   - Chiamare una volta con `VSEDITPROPID_ViewGeneral_ColorCategory`come argomento.

   - Chiamare una volta con `VSEDITPROPID_ViewGeneral_FontCategory` come argomento.

     Questo imposta ed espone i servizi di tipi di carattere e colori predefiniti come proprietà della finestra.

## <a name="example"></a>Esempio
 Nell'esempio seguente avvia l'uso di colori e tipi di carattere predefiniti.

```cpp
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

- [Usare i tipi di carattere e colori](../extensibility/using-fonts-and-colors.md)
- [Ottenere le informazioni di carattere e colori per la colorazione del testo](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [Accesso archiviate le impostazioni di carattere e colori](../extensibility/accessing-stored-font-and-color-settings.md)
- [Panoramica di carattere e colori](../extensibility/font-and-color-overview.md)