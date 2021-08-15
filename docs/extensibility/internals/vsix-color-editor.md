---
title: Editor colori VSIX | Microsoft Docs
description: Informazioni sullo strumento editor colori Visual Studio estensione, che consente di creare e modificare colori personalizzati per Visual Studio e generare chiavi di risorse del tema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e19105a9b769810011b5ae3871a3cae03e2bd48611087244fecf5ed40734067a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275099"
---
# <a name="vsix-color-editor"></a>Editor dei colori VSIX
Lo Visual Studio Editor colori estensioni consente di creare e modificare colori personalizzati per Visual Studio. Lo strumento può anche generare chiavi di risorse del tema in modo che i colori possano essere usati nel codice. Questo strumento è utile per creare colori per un'Visual Studio che supporta il tema. Questo strumento può aprire i file con estensione pkgdef e .xml file. Visual Studio temi (file con estensione vstheme) possono essere usati con l'editor colori dell'estensione Visual Studio modificando l'estensione del file in .xml. Inoltre, i file vstheme possono essere importati in un file .xml corrente.

 ![Immagine principale dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-hero.png "Immagine principale dell'editor dei colori VSIX")

 **File di definizione del pacchetto**

 I file di definizione del pacchetto (con estensione pkgdef) sono i file che definiscono i temi. I colori stessi vengono archiviati nei .xml tema, che vengono compilati in un file con estensione pkgdef. I file con estensione pkgdef vengono distribuiti Visual Studio percorsi ricercabili, elaborati in fase di esecuzione e uniti insieme per definire i temi.

 **Token di colore**

 Un token di colore è costituito da quattro elementi:

- **Nome categoria:** Raggruppamento logico per un set di colori. Usare un nome di categoria esistente se sono già presenti colori specifici dell'elemento dell'interfaccia utente desiderato o un gruppo di elementi dell'interfaccia utente.

- **Nome token:** Nome descrittivo per il token di colore e i set di token. I set includono nomi di token di sfondo e primo piano (testo) e tutti i relativi stati, che devono essere denominati in modo che sia facile identificare le coppie e gli stati a cui si applicano.

- **Valori di colore (o tonalità):** Necessario per ogni tema colorato. Creare sempre valori di colore di sfondo e testo in coppie. I colori vengono associati per lo sfondo/primo piano in modo che il colore del testo (primo piano) sia sempre leggibile rispetto al colore di sfondo su cui viene disegnato. Questi colori sono collegati e verranno usati insieme nell'interfaccia utente. Se lo sfondo non è destinato all'uso con il testo, non definire un colore di primo piano.

- **Nome colore di sistema:** Per l'uso in schermi a contrasto elevato.

## <a name="how-to-use-the-tool"></a>Procedura: utilizzare lo strumento
 Per quanto possibile, e laddove appropriato, i colori Visual Studio esistenti devono essere riutilizzati invece di crearne di nuovi. Tuttavia, nei casi in cui non è definito alcun colore appropriato, è necessario creare colori personalizzati per mantenere compatibili i tema dell'estensione.

 **Creazione di nuovi token di colore**

 Per creare colori personalizzati usando l'editor Visual Studio colori dell'estensione, seguire questa procedura:

1. Determinare i nomi di categoria e token per i nuovi token di colore.

2. Scegliere le tonalità che l'elemento dell'interfaccia utente userà per ogni tema e il colore di sistema per Contrasto elevato.

3. Usare l'editor colori per creare nuovi token di colore.

4. Usare i colori in un'Visual Studio predefinita.

5. Testare le modifiche in Visual Studio.

   **Passaggio 1: Determinare i nomi di categoria e token per i nuovi token di colore.**

   Lo schema di denominazione preferito per un oggetto VSColor è **[Categoria] [Tipo di interfaccia utente] [Stato]**. Non usare la parola "color" nei nomi VSColor, perché è ridondante.

   I nomi delle categorie forniscono raggruppamenti logici e devono essere definiti nel modo più ristretto possibile. Ad esempio, il nome di una singola finestra degli strumenti può essere un nome di categoria, ma il nome di un'intera business unit o team di progetto non lo è. Il raggruppamento delle voci in categorie consente di evitare confusione tra i colori con lo stesso nome.

   Un nome di token deve indicare chiaramente il tipo di elemento e le situazioni, o "stato", per cui verrà applicato il colore. Ad esempio, il [tipo di interfaccia **utente]** di un suggerimento dati attivo può essere denominato "**Suggerimento** dati " e **[Stato]** può essere denominato "**Attivo**", con il nome di colore "**DataTipActive**". Poiché i suggerimenti dati hanno testo, è necessario definire sia un colore di primo piano che un colore di sfondo. Usando un abbinamento sfondo/primo piano, l'editor colori creerà automaticamente i colori "**DataTipActive**" per lo sfondo e "**DataTipActiveText**" per il primo piano.

   Se la parte dell'interfaccia utente ha un solo stato, la parte **[State]** del nome può essere omessa. Ad esempio, se una casella di ricerca ha un bordo e non è presente alcuna modifica dello stato che influisce sul colore del bordo, il nome per il token di colore del bordo può essere semplicemente denominato **"SearchBoxBorder".**

   Alcuni nomi di stato comuni includono:

- Attivo

- Inattivo

- MouseOver

- Mousedown

- Opzione selezionata

- Con stato attivo

  Esempi di alcuni nomi di token per parti di un controllo elemento elenco:

- ListItem

- ListItemBorder

- ListItemMouseOver

- ListItemMouseOverBorder

- ListItemSelected

- ListItemSelectedBorder

- ListItemDisabled

- ListItemDisabledBorder

  **Passaggio 2: scegliere le tonalità che verranno usate dall'elemento dell'interfaccia utente per ogni tema e il colore di sistema per Contrasto elevato.**

  Quando si scelgono colori personalizzati per l'interfaccia utente, selezionare un elemento dell'interfaccia utente esistente simile e usarne i colori come base. I colori per gli elementi dell'interfaccia utente predefiniti sono stati sottoposti a revisione e test, quindi avranno un aspetto appropriato e si comporteranno correttamente in tutti i temi.

  **Passaggio 3: Usare l'editor colori per creare nuovi token di colore.**

  Avviare l'editor colori e aprire o creare un nuovo file di colori del tema .xml personalizzato. Selezionare **Modifica > nuovo colore** dal menu. Verrà visualizzata una finestra di dialogo per specificare la categoria e uno o più nomi per le voci di colore all'interno di tale categoria:

  ![Nuovo colore dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-new-color.png "Nuovo colore dell'editor dei colori VSIX")

  Selezionare una categoria esistente oppure selezionare **Nuova categoria** per creare una nuova categoria. Verrà visualizzata un'altra finestra di dialogo che crea un nuovo nome di categoria:

  ![Nuova categoria dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-new-category.png "Nuova categoria dell'editor dei colori VSIX")

  La nuova categoria sarà quindi disponibile nel menu a discesa **Nuova** categoria colore. Dopo aver scelto una categoria, immettere un nome per ogni riga per ogni nuovo token di colore e selezionare "Crea" al termine:

  ![Nuovo colore riempito dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "Nuovo colore riempito dell'editor dei colori VSIX")

  I valori dei colori vengono visualizzati in coppie sfondo/primo piano, con "Nessuno" che indica che il colore non è stato definito. Nota: se un colore non ha una coppia colore testo/sfondo, è necessario definire solo lo sfondo.

  ![Valori di colore dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "Valori di colore dell'editor dei colori VSIX")

  Per modificare un token di colore, selezionare una voce di colore per il tema (colonna) del token. Aggiungere il valore del colore digitando un valore di colore esadecimale in formato ARGB a 8 cifre, immettendo un nome di colore di sistema nella cella oppure usando il menu a discesa per selezionare il colore desiderato tramite un set di dispositivi di scorrimento dei colori o un elenco di colori di sistema.

  ![Modifica del colore dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-edit-color.png "Modifica del colore dell'editor dei colori VSIX")

  ![Sfondo dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-background.png "Sfondo dell'editor dei colori VSIX")

  Per i componenti che non devono visualizzare il testo, immettere un solo valore di colore: il colore di sfondo. In caso contrario, immettere i valori per lo sfondo e il colore del testo, separati da una barra.

  Quando si immettono valori per Contrasto elevato, immettere nomi di Windows di sistema validi. Non immettere valori ARGB hardcoded. È possibile visualizzare un elenco di nomi di colori di sistema validi selezionando "Sfondo: Sistema" o "Primo piano: Sistema" dai menu a discesa dei valori dei colori. Quando si creano elementi con componenti di testo, usare la coppia di colori di sistema di sfondo/testo corretta oppure il testo potrebbe essere illeggibile.

  Al termine della creazione, dell'impostazione e della modifica dei token di colore, salvarli nel formato .xml o pkgdef desiderato. I token di colore con uno sfondo o un set di primo piano verranno salvati come colori vuoti in .xml, ma eliminati in formato PKGDEF. Se si tenta di salvare i colori vuoti in un file con estensione pkgdef, verrà visualizzata una finestra di dialogo che segnala una potenziale perdita di colore.

  **Passaggio 4: Usare i colori in un'Visual Studio predefinita.**

  Dopo aver definito i nuovi token di colore, includere il file con estensione pkgdef nel file di progetto con "Build Action" impostato su "Content" e "Include in VSIX" impostato su "True".

  ![File pkgdef dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "File pkgdef dell'editor dei colori VSIX")

  Nell'editor Visual Studio colori dell'estensione scegliere File > Visualizza codice risorsa per visualizzare il codice usato per accedere ai colori personalizzati nell'interfaccia utente basata su WPF.

  ![Visualizzatore del codice delle risorse dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "Visualizzatore del codice delle risorse dell'editor dei colori VSIX")

  Includere questo codice in una classe statica nel progetto. Un riferimento a **Microsoft.VisualStudio.Shell. \<VSVersion>.0.dll** deve essere aggiunto al progetto per usare il **tipo ThemeResourceKey.**

```csharp
namespace MyCustomColors
{
    public static class MyCategory
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");

        private static ThemeResourceKey _MyColor1ColorKey;
        private static ThemeResourceKey _MyColor1BrushKey;
        private static ThemeResourceKey _MyColor1TextColorKey;
        private static ThemeResourceKey _MyColor1TextBrushKey;
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }
        #endregion
    }
}
```

 Ciò consente l'accesso ai colori nel codice XAML e consente all'interfaccia utente di rispondere alle modifiche del tema.

```xaml
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:ns="clr-namespace:MyCustomColors">
  <Grid>
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"
      >Sample Text</TextBlock>

  </Grid>
</UserControl>
```

 **Passaggio 5: Testare le modifiche in Visual Studio.**

 L'editor colori può applicare temporaneamente token di colore alle istanze in esecuzione di Visual Studio per visualizzare le modifiche in tempo reale ai colori senza ricompilare il pacchetto di estensione. A tale scopo, fare clic sul pulsante "Apply this theme to running Visual Studio windows" (Applica questo tema all'esecuzione Visual Studio finestre) nell'intestazione di ogni colonna del tema. Questo tema temporaneo verrà chiuso alla chiusura dell'Editor colori VSIX.

 ![Applicazione dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-apply.png "Applicazione dell'editor dei colori VSIX")

 Per rendere permanenti le modifiche, ricompilare e ridistribuire l'estensione Visual Studio dopo aver aggiunto i nuovi colori al file con estensione pkgdef e aver scritto il codice che userà tali colori. La ricompilazione Visual Studio'estensione consente di unire i valori del Registro di sistema per i nuovi colori nel resto dei temi. Riavviare quindi Visual Studio, visualizzare l'interfaccia utente e verificare che i nuovi colori vengano visualizzati come previsto.

## <a name="notes"></a>Note
 Questo strumento è progettato per la creazione di colori personalizzati per i temi Visual Studio preesistenti o per la modifica dei colori di un tema Visual Studio personalizzato. Per creare temi personalizzati Visual Studio, scaricare [l'Visual Studio Editor](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) tema colori dalla raccolta Visual Studio estensioni.

## <a name="sample-output"></a>Output di esempio
 **Output dei colori XML**

 Il .xml file generato dallo strumento sarà simile al seguente:

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">
      <Color Name="ColorName1">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
      <Color Name="ColorName2">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
        <Foreground Type="CT_RAW" Source="FF000000" />
      </Color>
      <Color Name="ColorName3">
        <Background Type="CT_RAW" Source="FFFF0000" />
      </Color>
      <Color Name="ColorName4">
        <Background Type="CT_RAW" Source="FF000088" />
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
    </Category>
  </Theme>
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>
</Themes>

```

 **Output dei colori PKGDEF**

 Il file con estensione pkgdef generato dallo strumento sarà simile al seguente:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]
"Data"=hex:...

```

 **Wrapper delle chiavi di risorsa C#**

 Le chiavi delle risorse di colore generate dallo strumento saranno simili alle seguenti:

```csharp
namespace MyNamespace
{
    public static class MyColors
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.

        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }

        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }

        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }
        #endregion
    }
}
```

 **Wrapper del dizionario risorse WPF**

 Le chiavi **di Colore ResourceDictionary** generate dallo strumento saranno simili alle seguenti:

```xaml
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:colors="clr-namespace:MyNamespace">

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />
</ResourceDictionary>
```
