---
title: Abilitare il test codificato dell'interfaccia utente per i controlli
description: Informazioni su come implementare il supporto per il framework di test codificati dell'interfaccia utente per rendere il controllo più testabile.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d75e6debf4fb50be2d144f0843e6c0be6a84a76c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628163"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Abilitare test codificati dell'interfaccia utente per i controlli

È utile implementare il supporto del framework dei test codificati dell'interfaccia utente per facilitare i test dei controlli. È possibile aggiungere gradualmente livelli crescenti di supporto. Iniziare supportando la registrazione, la riproduzione e la convalida delle proprietà. Partendo da queste basi, abilitare il generatore di test codificato dell'interfaccia utente per riconoscere le proprietà personalizzate dei controlli. Specificare classi personalizzate per accedere a tali proprietà dal codice generato. È anche possibile consentire al generatore di test codificati dell'interfaccia utente di acquisire le azioni nella modalità che più si avvicina di più allo scopo dell'azione registrata.

! Diagramma che illustra come le classi in ChartControl vengono estese tramite la classe CreateAccessabilityInstance alle classi in ChartControlExtensionPackage. (.. /test/media/cuit_full.png)

[!INCLUDE[coded-ui-test-deprecation](../test/includes/coded-ui-test-deprecation.md)]

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a>Supportare registrazione, riproduzione e convalida delle proprietà implementando l'accessibilità

Il generatore di test codificati dell'interfaccia utente acquisisce informazioni sui controlli intercettati durante la registrazione e quindi genera il codice per riprodurre quella sessione. Se il controllo non supporta l'accessibilità, il generatore di test codificati dell'interfaccia utente acquisisce le azioni, come ad esempio i clic del mouse, usando le coordinate dello schermo. Quando il test viene riprodotto, il codice generato emette le azioni nelle stesse coordinate dello schermo. Se, quando il test viene riprodotto, il controllo viene visualizzato in un punto diverso dello schermo, l'azione da parte del codice generato non riuscirà. Se non si implementa l'accessibilità per il controllo, è possibile che i test abbiano esito negativo se vengono riprodotti in configurazioni di schermo diverse, in ambienti diversi o quando il layout dell'interfaccia utente viene modificato.

![Screenshot della finestra di registrazione nel generatore di test codificati dell'interfaccia utente. Il pulsante Sospendi è evidenziato e il client Fare clic su "ChartControl" viene visualizzato in una descrizione comando.](../test/media/cuit_recordnosupport.png)

Se si implementa l'accessibilità, il generatore di test codificati dell'interfaccia utente la userà per acquisire informazioni sul controllo quando registra un test. Quindi, quando si esegue il test, il codice generato riprodurrà tali eventi sul controllo, anche se questo si trova altrove nell'interfaccia utente. Gli autori del test possono creare le asserzioni anche usando le proprietà di base del controllo.

![Screenshot della finestra di registrazione nel generatore di test codificati dell'interfaccia utente. Il pulsante Sospendi è evidenziato e in una descrizione comando viene visualizzata l'etichetta Fare clic su "A".](../test/media/cuit_record.png)

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Per supportare registrazione e riproduzione, convalida delle proprietà e navigazione per un controllo Windows Form
Implementare l'accessibilità per il controllo come descritto nella procedura seguente e descritto in dettaglio in <xref:System.Windows.Forms.AccessibleObject>.

![Diagramma delle classi in ChartControl che mostra la relazione tra CreateAccessabilityInstance e la classe ChartControl.CurveLegend.](../test/media/cuit_accessible.png)

1. Implementare una classe che derivi da <xref:System.Windows.Forms.Control.ControlAccessibleObject> ed eseguire l'override della proprietà <xref:System.Windows.Forms.Control.AccessibilityObject%2A> per restituire un oggetto della classe.

    ```csharp
    public partial class ChartControl : UserControl
    {
        // Overridden to return the custom AccessibleObject for the control.
        protected override AccessibleObject CreateAccessibilityInstance()
        {
            return new ChartControlAccessibleObject(this);
        }

        // Inner class ChartControlAccessibleObject represents accessible information
        // associated with the ChartControl and is used when recording tests.
        public class ChartControlAccessibleObject : ControlAccessibleObject
        {
            ChartControl myControl;
            public ChartControlAccessibleObject(ChartControl ctrl)
                : base(ctrl)
            {
                myControl = ctrl;
            }
        }
    }
    ```

2. Eseguire l'override dei metodi e delle proprietà <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> e <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> dell'oggetto accessibile.

3. Implementare un altro oggetto accessibilità per il controllo figlio ed eseguire l'override della proprietà <xref:System.Windows.Forms.Control.AccessibilityObject%2A> del controllo figlio per restituire tale oggetto accessibilità.

4. Eseguire l'override delle proprietà e dei metodi <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A> e <xref:System.Windows.Forms.AccessibleObject.Select%2A> per l'oggetto accessibilità del controllo figlio.

> [!NOTE]
> Questo argomento inizia con l'esempio di accessibilità in <xref:System.Windows.Forms.AccessibleObject> e si basa quindi su tale esempio nelle procedure restanti. Se si vuole creare una versione funzionante dell'esempio di accessibilità, creare un'applicazione console e quindi sostituire il codice in *Program.cs* con il codice di esempio. Aggiungere riferimenti a oggetti Accessibility, System.Drawing e System.Windows.Forms. Modificare **Incorpora tipi di interoperabilità** per l'accessibilità impostandolo su **False** per eliminare l'avviso di compilazione. È possibile modificare il tipo di output del progetto da **Applicazione console** ad **Applicazione Windows** in modo che non venga visualizzata alcuna finestra della console quando si esegue l'applicazione.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a>Supportare la convalida delle proprietà personalizzate implementando un provider di proprietà

Dopo aver implementato il supporto di base per la registrazione, la riproduzione e la convalida delle proprietà, è possibile rendere disponibili le proprietà personalizzate del controllo ai test codificati dell'interfaccia utente mediante l'implementazione di un plug-in <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>. La procedura seguente, ad esempio, crea un provider di proprietà che consente ai test codificati dell'interfaccia utente di accedere alla proprietà di stato dei controlli figlio del controllo CurveLegend del grafico:

![Screenshot della finestra principale del generatore di test codificati dell'interfaccia utente parzialmente coperta da una finestra Aggiungi asserzioni con la proprietà State di un controllo Text selezionata.](../test/media/cuit_customprops.png)

### <a name="to-support-custom-property-validation"></a>Per supportare la convalida delle proprietà personalizzate

![Diagramma delle classi in ChartControl e ChartControlExtension con le classi ChartControlExtensionPackage e ChartControlIPropertyProvider evidenziate.](../test/media/cuit_props.png)

1. Eseguire l'override della proprietà <xref:System.Windows.Forms.AccessibleObject.Description%2A> dell'oggetto accessibile CurveLegend per passare valori di proprietà avanzate nella stringa di descrizione. Se si specificano più valori, separarli con il punto e virgola (;).

    ```csharp
    public class CurveLegendAccessibleObject : AccessibleObject
    {
        // add the state property value to the description
        public override string Description
        {
            get
            {
                // Add ";" and the state value to the end
                // of the curve legend's description
                return "CurveLegend; " + State.ToString();
            }
        }
    }
    ```

1. Generare un pacchetto di estensione di test dell'interfaccia utente per il controllo creando un progetto di libreria di classi. Aggiungere riferimenti ad Accessibility, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common e Microsoft.VisualStudio.TestTools.Extension. Modificare il valore per **Incorpora tipi di interoperabilità** per l'accessibilità impostandolo su **False**.

1. Aggiungere una classe di provider di proprietà che sia derivata da <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>:

    ```csharp
    using System;
    using System.Collections.Generic;
    using Accessibility;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        public class ChartControlPropertyProvider : UITestPropertyProvider
        {
        }
    }
    ```

1. Implementare il provider di proprietà inserendo i nomi di proprietà e i descrittori di proprietà in un oggetto <xref:System.Collections.Generic.Dictionary%602>.

1. Eseguire l'override di <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> per indicare che l'assembly fornisce supporto specifico del controllo per il controllo e per i relativi elementi figlio.

1. Eseguire l'override dei rimanenti metodi astratti di <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>

1. Aggiungere una classe del pacchetto di estensione che sia derivata da <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Definire l'attributo `UITestExtensionPackage` per l'assembly.

1. Nella classe del pacchetto di estensione, eseguire l'override di <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> per restituire la classe del provider di proprietà, quando ne è richiesto uno.

1. Eseguire l'override delle proprietà e dei metodi astratti rimanenti dell'oggetto <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Compilare i file binari e copiarli in *%Programmi%\File comuni\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Questo pacchetto di estensione viene applicato a qualsiasi controllo di tipo "Text". Se si stanno testando più controlli dello stesso tipo, è necessario testarli separatamente in modo da poter definire quali pacchetti di estensione vengono distribuiti quando si registrano i test.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a>Supportare la generazione di codice implementando una classe per accedere alle proprietà personalizzate

Quando il generatore di test codificati dell'interfaccia utente genera il codice da una registrazione della sessione, usa la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> per accedere ai controlli dell'utente.

Se è stato implementato un provider di proprietà per offrire accesso alle proprietà personalizzate del controllo, è possibile aggiungere una classe specializzata per accedere a tali proprietà. L'aggiunta di una classe specializzata semplifica il codice generato.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Per aggiungere una classe specializzata per accedere al proprio controllo

![Diagramma delle classi in ChartControl e ChartControlExtension con la classe CurveLegend evidenziata in ChartControlExtensionPackage.](../test/media/cuit_codegen.png)

1. Implementare una classe che sia derivata da <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> e aggiungere il tipo del controllo alla raccolta di proprietà di ricerca nel costruttore.

1. Implementare le proprietà personalizzate del controllo come proprietà della classe.

1. Eseguire l'override del metodo <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> del provider di proprietà per restituire il tipo della nuova classe per i controlli figlio dell'oggetto CurveLegend.

1. Eseguire l'override del metodo <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> del provider di proprietà per restituire il tipo del metodo PropertyNames della nuova classe.

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a>Supportare le azioni sensibili allo scopo implementando un filtro azioni

Quando Visual Studio registra un test, acquisisce ogni evento di mouse e tastiera. Tuttavia, in alcuni casi, lo scopo dell'azione può perdersi nella serie di eventi di mouse e tastiera. Ad esempio, se il controllo supporta il completamento automatico, lo stesso set di eventi di mouse e tastiera può comportare un valore diverso quando il test viene riprodotto in un ambiente diverso. È possibile aggiungere un plug-in del filtro azioni che sostituisce la serie di eventi di mouse e tastiera con una sola azione. In questo modo, è possibile sostituire la sequenza di eventi di mouse e tastiera che seleziona un valore con una sola azione che imposta il valore. Questa operazione consente di proteggere i test codificati dell'interfaccia utente dalle differenze nel completamento automatico da un ambiente a un altro.

### <a name="to-support-intent-aware-actions"></a>Per supportare le azioni sensibili allo scopo

![Diagramma delle classi ChartControl e ChartControlExtensionPackage con la classe ChartControlActionFilter evidenziata in ChartControlExtensionPackage.](../test/media/cuit_actions.png)

1. Implementare una classe di filtro azioni che sia derivata da [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)), eseguendo l'override delle proprietà [ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Category](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [Enabled](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)), [Group](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) e [Name](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110)).

1. Eseguire l'override di [ProcessRule](/previous-versions/visualstudio/visual-studio-2012/dd987281(v=vs.110)). In questo esempio si sostituisce un'azione di doppio clic con un'azione di clic singolo.

1. Aggiungere il filtro azioni al metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> del pacchetto di estensione.

1. Compilare i file binari e copiarli in *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Il filtro azioni non dipende dall'implementazione di accessibilità o dal provider di proprietà.

## <a name="debug-your-property-provider-or-action-filter"></a>Eseguire il debug del provider di proprietà o del filtro azioni

Il provider di proprietà e il filtro azioni vengono implementati in un pacchetto di estensione. Il generatore di test esegue il pacchetto di estensione in un processo separato dall'applicazione.

### <a name="to-debug-your-property-provider-or-action-filter"></a>Per eseguire il debug del provider di proprietà o del filtro azioni

1. Compilare la versione di debug del pacchetto di estensione copiare i file *.dll* e *pdb* in *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

2. Eseguire l'applicazione (non nel debugger).

3. Eseguire il generatore di test codificati dell'interfaccia utente.

     `codedUITestBuilder.exe  /standalone`

4. Associare il debugger al processo codedUITestBuilder.

5. Impostare i punti di interruzione nel codice.

6. Nel generatore di test codificati dell'interfaccia utente creare le asserzioni per verificare il provider di proprietà e registrare azioni per verificare i filtri azioni.

## <a name="see-also"></a>Vedi anche

- <xref:System.Windows.Forms.AccessibleObject>
- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
