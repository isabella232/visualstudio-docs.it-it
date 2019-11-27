---
title: Abilitare il test codificato dell'interfaccia utente per i controlli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 24
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 331dabfe8e219383fdc04187482b17b9048886a9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302575"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Abilitare il test codificato dell'interfaccia utente per i controlli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il controllo può essere testato più facilmente se si implementa il supporto per il framework dei test codificati dell'interfaccia utente. È possibile aggiungere gradualmente livelli crescenti di supporto. Si può iniziare supportando la registrazione, la riproduzione e la convalida delle proprietà. Sarà quindi possibile consentire al generatore di test codificati dell'interfaccia utente di riconoscere le proprietà personalizzate del controllo, nonché fornire classi personalizzate per accedere a tali proprietà dal codice generato. È anche possibile consentire al generatore di test codificati dell'interfaccia utente di acquisire le azioni nella modalità che più si avvicina di più allo scopo dell'azione registrata.

 **Contenuto dell'argomento:**

1. [Supportare registrazione, riproduzione e convalida delle proprietà implementando l'accessibilità](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)

2. [Supportare la convalida delle proprietà personalizzate implementando un provider di proprietà](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)

3. [Supportare la generazione di codice implementando una classe per accedere alle proprietà personalizzate](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)

4. [Supportare le azioni sensibili allo scopo implementando un filtro azioni](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)

   ![CUIT&#95;completo](../test/media/cuit-full.png "CUIT_Full")

## <a name="recordandplayback"></a>Supportare registrazione, riproduzione e convalida delle proprietà implementando l'accessibilità
 Il generatore di test codificati dell'interfaccia utente acquisisce informazioni sui controlli intercettati durante la registrazione e quindi genera il codice per riprodurre quella sessione. Se il controllo non supporta l'accessibilità, il generatore di test codificati dell'interfaccia utente acquisisce le azioni (quali i clic del mouse) usando le coordinate dello schermo. Quando il test viene riprodotto, il codice generato emetterà i clic del mouse nelle stesse coordinate dello schermo. Se, quando il test viene riprodotto, il controllo viene visualizzato in un punto diverso dello schermo, l'azione nel controllo da parte del codice generato non riuscirà. Ciò può dare luogo a errori se il test viene riprodotto in diverse configurazioni dello schermo, in ambienti diversi o dopo l'applicazione di modifiche al layout dell'interfaccia utente.

 ![RecordNoSupport&#95;cuit](../test/media/cuit-recordnosupport.png "CUIT_RecordNoSupport")

 Se si implementa l'accessibilità, tuttavia, il generatore di test codificati la userà per acquisire informazioni sul controllo quando registra un test e genera il codice. Quindi, quando si esegue il test, il codice generato riprodurrà tali eventi sul controllo, anche se questo si trova altrove nell'interfaccia utente. Gli autori del test potranno inoltre creare le asserzioni usando le proprietà di base del controllo.

 ![Record&#95;cuit](../test/media/cuit-record.png "CUIT_Record")

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Per supportare registrazione e riproduzione, convalida della proprietà e navigazione per un controllo Windows form
 Implementare l'accessibilità per il controllo come descritto nella procedura seguente e descritto in dettaglio in <xref:System.Windows.Forms.AccessibleObject>.

 ![CUIT&#95;accessibile](../test/media/cuit-accessible.png "CUIT_Accessible")

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
> Questo argomento inizia con l'esempio di accessibilità in <xref:System.Windows.Forms.AccessibleObject> in questa procedura e si basa quindi su tale esempio nelle procedure restanti. Se si vuole creare una versione funzionante dell'esempio di accessibilità, creare un'applicazione console e quindi sostituire il codice in Program.cs con il codice di esempio. Sarà necessario aggiungere riferimenti a Accessibilità, System.Drawing e System.Windows.Forms. Per eliminare un avviso di compilazione, è necessario impostare su **False** l'opzione **Incorpora tipi di interoperabilità** per l'accessibilità. È possibile modificare il tipo di output del progetto da **Applicazione console** ad **Applicazione Windows** in modo che non venga visualizzata alcuna finestra della console quando si esegue l'applicazione.

## <a name="customproprties"></a> Supportare la convalida delle proprietà personalizzate implementando un provider di proprietà
 Dopo aver implementato il supporto di base per la registrazione, riproduzione e convalida delle proprietà, è possibile rendere disponibili le proprietà personalizzate del controllo ai test codificati dell'interfaccia utente mediante l'implementazione di un plug-in <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>. La procedura seguente, ad esempio, crea un provider di proprietà che consente ai test codificati dell'interfaccia utente di accedere alla proprietà di stato dei controlli figlio del controllo CurveLegend del grafico.

 ![CustomProps&#95;cuit](../test/media/cuit-customprops.png "CUIT_CustomProps")

### <a name="to-support-custom-property-validation"></a>Per supportare la convalida delle proprietà personalizzate
 ![Props CUIT&#95;](../test/media/cuit-props.png "CUIT_Props")

1. Eseguire l'override della proprietà <xref:System.Windows.Forms.AccessibleObject.Description%2A> dell'oggetto accessibile CurveLegend per passare valori di proprietà avanzate nella stringa di descrizione, separati dalla descrizione principale (e tra loro se si stanno implementando più proprietà) mediante caratteri di punto e virgola (;).

    ```csharp
    public class CurveLegendAccessibleObject : AccessibleObject
    {
        // add the state property value to the description
        public override string Description
        {
            get
            {
                // Add “;” and the state value to the end
                // of the curve legend’s description
                return "CurveLegend; " + State.ToString();
            }
        }
    }
    ```

2. Creare un pacchetto di estensione di test dell'interfaccia utente per il controllo creando un progetto libreria di classi e aggiungere riferimenti ad Accessibility, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common e Microsoft.VisualStudio.TestTools.Extension. Modificare il valore per **Incorpora tipi di interoperabilità** per l'accessibilità impostandolo su **False**.

3. Aggiungere una classe di provider di proprietà che sia derivata da <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>.

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

4. Implementare il provider di proprietà inserendo i nomi di proprietà e i descrittori di proprietà in un oggetto <xref:System.Collections.Generic.Dictionary%602>.

    ```csharp
    // Define a map of property descriptors for CurveLegend
    private static Dictionary<string, UITestPropertyDescriptor> curveLegendPropertiesMap = null;
    private static Dictionary<string, UITestPropertyDescriptor> CurveLegendPropertiesMap
    {
        get
        {
            if (curveLegendPropertiesMap == null)
            {
                UITestPropertyAttributes read =
                    UITestPropertyAttributes.Readable |
                    UITestPropertyAttributes.DoNotGenerateProperties;
                curveLegendPropertiesMap =
                    new Dictionary<string, UITestPropertyDescriptor>
                        (StringComparer.OrdinalIgnoreCase);
                curveLegendPropertiesMap.Add("State",
                    new UITestPropertyDescriptor(typeof(string), read));
            }
            return curveLegendPropertiesMap;
        }
    }

    // return the property descriptor
    public override UITestPropertyDescriptor GetPropertyDescriptor(UITestControl uiTestControl, string propertyName)
    {
        return CurveLegendPropertiesMap[propertyName];
    }

    // return the property names
    public override ICollection<string> GetPropertyNames(UITestControl uiTestControl)
    {
        if (uiTestControl.ControlType.NameEquals("Chart") || uiTestControl.ControlType.NameEquals("Text"))
        {
            // the keys of the property map are the collection of property names
            return CurveLegendPropertiesMap.Keys;
        }

        // this is not my control
        throw new NotSupportedException();
    }

    // Get the property value by parsing the accessible description
    public override object GetPropertyValue(UITestControl uiTestControl, string propertyName)
    {
        if (String.Equals(propertyName, "State", StringComparison.OrdinalIgnoreCase))
        {
            object[] native = uiTestControl.NativeElement as object[];
            IAccessible acc = native[0] as IAccessible;

            string[] descriptionTokens = acc.accDescription.Split(new char[] { ';' });
            return descriptionTokens[1];
        }

        // this is not my control
        throw new NotSupportedException();
    }
    ```

5. Eseguire l'override di <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> per indicare che l'assembly fornisce supporto specifico del controllo per il controllo e per i relativi elementi figlio.

    ```csharp
    public override int GetControlSupportLevel(UITestControl uiTestControl)
    {
        // For MSAA, check the control type
        if (string.Equals(uiTestControl.TechnologyName, "MSAA",
            StringComparison.OrdinalIgnoreCase) &&
            (uiTestControl.ControlType == "Chart"||uiTestControl.ControlType == "Text"))
        {
            return (int)ControlSupport.ControlSpecificSupport;
        }

        // This is not my control, so return NoSupport
        return (int)ControlSupport.NoSupport;
    }
    ```

6. Eseguire l'override dei rimanenti metodi astratti di <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>.

    ```csharp
    public override string[] GetPredefinedSearchProperties(Type specializedClass)
    {
        throw new NotImplementedException();
    }

    public override Type GetSpecializedClass(UITestControl uiTestControl)
    {
        throw new NotImplementedException();
    }

    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)
    {
        throw new NotImplementedException();
    }

    public override void SetPropertyValue(UITestControl uiTestControl, string propertyName, object value)
    {
        throw new NotImplementedException();
    }

    public override string GetPropertyForAction(UITestControl uiTestControl, UITestAction action)
    {
        throw new NotImplementedException();
    }

    public override string[] GetPropertyForControlState(UITestControl uiTestControl, ControlStates uiState, out bool[] stateValues)
    {
        throw new NotImplementedException();
    }

    ```

7. Aggiungere una classe del pacchetto di estensione che sia derivata da <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        internal class ChartControlExtensionPackage : UITestExtensionPackage
        {
        }
    }
    ```

8. Definire l'attributo `UITestExtensionPackage` per l'assembly.

    ```csharp
    [assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(
                    "ChartControlExtensionPackage",
                    typeof(ChartControlExtensionPackage.ChartControlExtensionPackage))]
    namespace ChartControlExtensionPackage
    {
       …
    ```

9. Nella classe del pacchetto di estensione, eseguire l'override di <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> per restituire la classe del provider di proprietà, quando ne è richiesto uno.

    ```csharp
    internal class ChartControlExtensionPackage : UITestExtensionPackage
    {
        public override object GetService(Type serviceType)
        {
            if (serviceType == typeof(UITestPropertyProvider))
            {
                if (propertyProvider == null)
                {
                    propertyProvider = new ChartControlPropertyProvider();
                }
                return propertyProvider;
            }
            return null;
        }

        private UITestPropertyProvider propertyProvider = null;
    }
    ```

10. Eseguire l'override delle proprietà e dei metodi astratti rimanenti dell'oggetto <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

    ```csharp

    public override void Dispose() { }

    public override string PackageDescription
    {
        get { return "Supports coded UI testing of ChartControl"; }
    }

    public override string PackageName
    {
        get { return "ChartControl Test Extension"; }
    }

    public override string PackageVendor
    {
        get { return "Microsoft (sample)"; }
    }

    public override Version PackageVersion
    {
        get { return new Version(1, 0); }
    }

    public override Version VSVersion
    {
        get { return new Version(10, 0); }
    }
    ```

11. Compilare i file binari e copiarli in **%Programmi%\File comuni\Microsoft Shared\VSTT\10.0\UITestExtensionPackages**.

> [!NOTE]
> Questo pacchetto di estensione verrà applicato a qualsiasi controllo di tipo "testo". Se si stanno testando più controlli dello stesso tipo, sarà necessario testarli separatamente e definire quali pacchetti di estensione vengono distribuiti quando si registrano i test.

## <a name="codegeneration"></a> Supportare la generazione di codice implementando una classe per accedere alle proprietà personalizzate
 Quando il generatore di test codificati dell'interfaccia utente genera il codice da una registrazione della sessione, usa la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> per accedere ai controlli dell'utente.

```csharp

      UITestControl uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.GetProperty("State").ToString());
```

 Se è stato implementato un provider di proprietà per fornire accesso alle proprietà personalizzate del controllo, è possibile aggiungere una classe specializzata per accedere a tali proprietà, in modo da semplificare il codice generato.

```csharp

      ControlLegend uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.State);
```

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Per aggiungere una classe specializzata per accedere al proprio controllo
 ![CodeGen&#95;cuit](../test/media/cuit-codegen.png "CUIT_CodeGen")

1. Implementare una classe che sia derivata da <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> e aggiungere il tipo del controllo alla raccolta di proprietà di ricerca nel costruttore.

    ```csharp
    public class CurveLegend:WinControl
    {
       public CurveLegend(UITestControl c) : base(c)
       {
          // The curve legend control is a “text” type of control
          SearchProperties.Add(
             UITestControl.PropertyNames.ControlType, "Text");
       }
    }
    ```

2. Implementare le proprietà personalizzate del controllo come proprietà della classe.

    ```csharp
    public virtual string State
    {
        get
        {
            return (string)GetProperty("State");
        }
    }
    ```

3. Eseguire l'override del metodo <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> del provider di proprietà per restituire il tipo della nuova classe per i controlli figlio dell'oggetto CurveLegend.

    ```csharp
    public override Type GetSpecializedClass(UITestControl uiTestControl)
    {
       if (uiTestControl.ControlType.NameEquals("Text"))
       {
          // This is text type of control. For my control,
          // that means it’s a curve legend control.
          return typeof(CurveLegend);
       }

       // this is not a curve legend control
       return null;
    }
    ```

4. Eseguire l'override del metodo <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> del provider di proprietà per restituire il tipo del metodo PropertyNames della nuova classe.

    ```csharp
    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)
    {
        if (uiTestControl.ControlType.NameEquals("Text"))
        {
          // This is text type of control. For my control,
          // that means it’s a curve legend control.
            return typeof(CurveLegend.PropertyNames);
        }

        // this is not a curve legend control
        return null;
    }
    ```

## <a name="intentawareactions"></a> Supportare le azioni sensibili allo scopo implementando un filtro azioni
 Quando Visual Studio registra un test, acquisisce ogni evento di mouse e tastiera. Tuttavia, in alcuni casi, lo scopo dell'azione può perdersi nella serie di eventi di mouse e tastiera. Ad esempio, se il controllo supporta il completamento automatico, lo stesso set di eventi di mouse e tastiera può comportare un valore diverso quando il test viene riprodotto in un ambiente diverso. È possibile aggiungere un plug-in del filtro azioni che sostituisce la serie di eventi di mouse e tastiera con una sola azione. In questo modo, è possibile sostituire la sequenza di eventi di mouse e tastiera derivanti dalla selezione di un valore con una sola azione che imposta il valore. Questa operazione consente di proteggere i test codificati dell'interfaccia utente dalle differenze nel completamento automatico da un ambiente a un altro.

### <a name="to-support-intent-aware-actions"></a>Per supportare le azioni sensibili allo scopo
 ![Azioni&#95;cuit](../test/media/cuit-actions.png "CUIT_Actions")

1. Implementare una classe di filtro azioni derivata da [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)), eseguendo l'override delle proprietà [ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Category](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [Enabled](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)), [Group](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) e [Name](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110)).

    ```csharp
    internal class MyActionFilter : UITestActionFilter
    {
       // If the user actions we are aggregating exceeds the time allowed,
       // this filter is not applied. (The timeout is configured when the
       // test is run.)
       public override bool ApplyTimeout
       {
          get { return true; }
       }

       // Gets the category of this filter. Categories of filters
       // are applied in priority order.
       public override UITestActionFilterCategory Category
       {
          get { return UITestActionFilterCategory.PostSimpleToCompoundActionConversion; }
       }

       public override bool Enabled
       {
          get { return true; }
       }

       public override UITestActionFilterType FilterType
       {
          // This action filter operates on a single action
          get { return UITestActionFilterType.Unary; }
       }

       // Gets the name of the group to which this filter belongs.
       // A group can be enabled/disabled using configuration file.
       public override string Group
       {
          get { return "ChartControlActionFilters"; }
       }

       // Gets the name of this filter.
       public override string Name
       {
          get { return "Convert Double-Click to Single-Click"; }
       }
    ```

2. Eseguire l'override di `UITestActionFilter.ProcessRule`. In questo esempio si sostituisce un'azione di doppio clic con un'azione di clic singolo.

    ```csharp
    public override bool ProcessRule(IUITestActionStack actionStack)
    {
        if (actionStack.Count > 0)
        {
            MouseAction lastAction = actionStack.Peek() as MouseAction;
            if (lastAction != null)
            {
                if (lastAction.UIElement.ControlTypeName.Equals(
                     ControlType.Text.ToString(),
                     StringComparison.OrdinalIgnoreCase))
                {
                    if(lastAction.ActionType == MouseActionType.DoubleClick)
                    {
                        // Convert to single click
                        lastAction.ActionType = MouseActionType.Click;
                    }
                }
            }
        }
        // Do not stop aggregation
        return false;
    }
    ```

3. Aggiungere il filtro azioni al metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> del pacchetto di estensione.

    ```csharp
    public override object GetService(Type serviceType)
    {
       if (serviceType == typeof(UITestPropertyProvider))
       {
          if (propertyProvider == null)
          {
             propertyProvider = new PropertyProvider();
          }
          return propertyProvider;
       }
       else if (serviceType == typeof(UITestActionFilter))
       {
          if (actionFilter == null)
          {
             actionFilter = new RadGridViewActionFilter();
          }
          return actionFilter;
       }
       return null;
    }
    ```

4. Compilare i file binari e copiarli in %ProgramFiles%\File comuni\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.

> [!NOTE]
> Il filtro azioni non dipende dall'implementazione di accessibilità o dal provider di proprietà.

## <a name="debug-your-property-provider-or-action-filter"></a>Eseguire il debug del provider di proprietà o del filtro azioni
 Il provider di proprietà e il filtro azioni sono distribuiti in un pacchetto di estensione che viene caricato ed eseguito dal generatore di test codificati dell'interfaccia utente in un processo distinto dall'applicazione.

#### <a name="to-debug-your-property-provider-or-action-filter"></a>Per eseguire il debug del provider di proprietà o del filtro azioni

1. Compilare la versione di debug del pacchetto di estensione copiare i file .dll e .pdb in %ProgramFiles%\File comuni\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.

2. Eseguire l'applicazione (non nel debugger).

3. Eseguire il generatore di test codificati dell'interfaccia utente.

     `codedUITestBuilder.exe  /standalone`

4. Associare il debugger al processo codedUITestBuilder.

5. Impostare i punti di interruzione nel codice.

6. Nel generatore di test codificati dell'interfaccia utente creare le asserzioni per verificare il provider di proprietà e registrare azioni per verificare i filtri azioni.

## <a name="external-resources"></a>Risorse esterne

### <a name="guidance"></a>Materiale sussidiario
 [Test per la distribuzione continua con Visual Studio 2012 – Capitolo 2: Unit Testing: Test interni](https://go.microsoft.com/fwlink/?LinkID=255188)

## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Forms.AccessibleObject>
- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
