---
title: Aggiornare Outlook aree del modulo quando viene eseguita la migrazione a .NET Framework 4.5
description: È necessario modificare il codice se il framework di destinazione di un progetto di componente aggiuntivo Outlook VSTO con un'area del modulo viene modificato in .NET Framework 4 o versione successiva.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 4237b4412a1175260643e7fe3e0ef9c89bb31540
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115005"
---
# <a name="update-outlook-form-regions-when-migrated-to-net-framework-45"></a>Aggiornare Outlook aree del modulo quando viene eseguita la migrazione a .NET Framework 4.5

  Se il framework di destinazione di un progetto di componente aggiuntivo VSTO per Outlook contenente un'area del modulo viene modificato in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario apportare modifiche all'area del modulo generato e a qualsiasi codice che crea istanze di alcune classi di aree del modulo in fase di esecuzione.

## <a name="update-the-generated-form-region-code"></a>Aggiornare il codice dell'area del modulo generato
 Se il framework di destinazione del progetto viene modificato in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario modificare il codice generato dell'area del modulo. Le modifiche da apportare cambiano a seconda che le aree del modulo siano progettate in Visual Studio o importate da Outlook. Per altre informazioni sulle differenze tra questi tipi di aree del modulo, vedere Creare Outlook [di modulo.](../vsto/creating-outlook-form-regions.md)

### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Per aggiornare il codice generato per un'area del modulo progettata in Visual Studio

1. Aprire il file code-behind dell'area del modulo nell'editor del codice. Il nome del file è *YourFormRegion.Designer.cs* o *YourFormRegion.Designer.vb*. Per visualizzare questo file nei progetti Visual Basic, fare clic sul pulsante **Mostra tutti i file** in **Esplora soluzioni**.

2. Modificare la dichiarazione della classe di aree del modulo in modo che derivi da <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> anziché da `Microsoft.Office.Tools.Outlook.FormRegionControl`.

3. Modificare il costruttore della classe di aree del modulo come illustrato negli esempi di codice seguenti.

     L'esempio di codice seguente illustra il costruttore di una classe di aree del modulo in un progetto destinato a .NET Framework 3.5.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.InitializeComponent();
    }
    ```

     L'esempio di codice seguente illustra il costruttore di una classe di aree del modulo in un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.InitializeComponent();
    }
    ```

4. Modificare la firma del metodo `InitializeManifest` come illustrato di seguito. Assicurarsi di non modificare il codice nel metodo perché rappresenta le impostazioni dell'area del modulo applicate nella finestra di progettazione. Nei progetti Visual C# è necessario espandere l'area denominata `Form Region Designer generated code` per visualizzare il metodo.

     L'esempio di codice seguente illustra la firma del metodo `InitializeManifest` in un progetto destinato a .NET Framework 3.5.

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest)
    {
        // Do not change code in this method.
    }
    ```

     L'esempio di codice seguente viene illustrata la firma del metodo `InitializeManifest` in un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest,
        ByVal factory As Microsoft.Office.Tools.Outlook.Factory)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest,
        Microsoft.Office.Tools.Outlook.Factory factory)
    {
        // Do not change code in this method.
    }
    ```

5. Aggiungere un nuovo elemento Area del modulo di Outlook al progetto. Aprire il file code-behind per la nuova area del modulo, individuare le classi *e YourNewFormRegion* nel file e copiare queste classi `Factory` negli `WindowFormRegionCollection` Appunti.

6. Eliminare la nuova area del modulo aggiunta al progetto.

7. Nel file code-behind dell'area del modulo che si sta aggiornando per funzionare nel progetto ridestinato individuare le classi *e YourOriginalFormRegion* e sostituirle con il codice copiato dalla nuova area del `Factory` `WindowFormRegionCollection` modulo.

8. Nelle classi *YourNewFormRegion* e cercare tutti i riferimenti alla classe YourNewFormRegion e modificare invece ogni riferimento alla `Factory` classe `WindowFormRegionCollection` *YourOriginalFormRegion.*  Ad esempio, se l'area del modulo che si vuole aggiornare è denominata `SalesDataFormRegion` e la nuova area del modulo creata nel passaggio 5 è denominata `FormRegion1`, impostare tutti i riferimenti di `FormRegion1` a `SalesDataFormRegion`.

#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Per aggiornare il codice generato per un'area del modulo importata da Outlook

1. Aprire il file code-behind dell'area del modulo nell'editor del codice. Il nome del file è *YourFormRegion.Designer.cs* o *YourFormRegion.Designer.vb*. Per visualizzare questo file nei progetti Visual Basic, fare clic sul pulsante **Mostra tutti i file** in **Esplora soluzioni**.

2. Modificare la dichiarazione della classe di aree del modulo in modo che derivi da <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> anziché da `Microsoft.Office.Tools.Outlook.ImportedFormRegion`.

3. Modificare il costruttore della classe di aree del modulo come illustrato negli esempi di codice seguenti.

     L'esempio di codice seguente illustra il costruttore di una classe di aree del modulo in un progetto destinato a .NET Framework 3.5.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

     L'esempio di codice seguente illustra la firma del costruttore di una classe di aree del modulo in un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

4. Per ogni riga di codice nel metodo `InitializeControls` che inizializza un controllo nella classe di aree del modulo, modificare il codice come illustrato di seguito.

     L'esempio di codice seguente illustra come inizializzare un controllo in un progetto destinato a .NET Framework 3.5. In questo codice, il metodo `GetFormRegionControl` ha un parametro di tipo che specifica il tipo del controllo restituito.

    ```vb
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")
    ```

    ```csharp
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");
    ```

     L'esempio di codice seguente illustra come inizializzare un controllo in un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. In questo codice, il metodo <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> non ha un parametro di tipo. È necessario sottoporre a cast il valore restituito nel tipo del controllo che si vuole inizializzare.

    ```vb
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)
    ```

    ```csharp
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");
    ```

5. Aggiungere un nuovo elemento Area del modulo di Outlook al progetto. Aprire il file code-behind per la nuova area del modulo, individuare le classi *e YourNewFormRegion* nel file e copiare queste classi `Factory` negli `WindowFormRegionCollection` Appunti.

6. Eliminare la nuova area del modulo aggiunta al progetto.

7. Nel file code-behind dell'area del modulo che si sta aggiornando per funzionare nel progetto ridestinato individuare le classi *e YourOriginalFormRegion* e sostituirle con il codice copiato dalla nuova area del `Factory` `WindowFormRegionCollection` modulo.

8. Nelle classi *YourNewFormRegion* e cercare tutti i riferimenti alla classe YourNewFormRegion e modificare invece ogni riferimento alla `Factory` classe `WindowFormRegionCollection` *YourOriginalFormRegion.*  Ad esempio, se l'area del modulo che si vuole aggiornare è denominata `SalesDataFormRegion` e la nuova area del modulo creata nel passaggio 5 è denominata `FormRegion1`, impostare tutti i riferimenti di `FormRegion1` a `SalesDataFormRegion`.

## <a name="instantiate-form-region-classes"></a>Creare un'istanza di classi di aree del modulo
 È necessario modificare il codice che crea dinamicamente istanze di alcune classi di aree del modulo. Nei progetti destinati a .NET Framework 3.5, è possibile creare direttamente istanze di classi di aree del modulo come `Microsoft.Office.Tools.Outlook.FormRegionManifest`. Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, queste classi sono interfacce di cui non è possibile creare istanze direttamente.

 Se il framework di destinazione del progetto viene modificato in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario creare istanze delle interfacce usando i metodi forniti dalla proprietà di `Globals.Factory`. Per altre informazioni sulla proprietà , vedere Accesso globale agli `Globals.Factory` oggetti in Office [progetti](../vsto/global-access-to-objects-in-office-projects.md).

 La tabella seguente elenca i tipi di area del modulo e il metodo da usare per creare istanze dei tipi nei progetti destinati [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive.

|Tipo|Metodo factory da usare|
|----------|---------------------------|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|

## <a name="see-also"></a>Vedi anche
- [Eseguire la Office soluzioni al .NET Framework 4 o versione successiva](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Creare aree Outlook modulo](../vsto/creating-outlook-form-regions.md)
