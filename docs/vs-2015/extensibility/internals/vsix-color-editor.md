---
title: Editor colori VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea5695c41b19cbd77c56a63f22b52fca5ee6f1eb
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295437"
---
# <a name="vsix-color-editor"></a>Editor dei colori VSIX
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lo strumento Editor colori estensione Visual Studio consente di creare e modificare colori personalizzati per Visual Studio. Lo strumento consente inoltre di generare chiavi di risorsa del tema in modo che i colori possano essere utilizzati nel codice. Questo strumento è utile per la creazione di colori per un'estensione di Visual Studio che supporta i temi. Questo strumento consente di aprire i file con estensione pkgdef e XML. I temi di Visual Studio (file con estensione vstheme) possono essere usati con l'Editor colori dell'estensione di Visual Studio modificando l'estensione del file in formato XML. Inoltre, i file con estensione vstheme possono essere importati in un file XML corrente.  
  
 ![Hero Editor colori VSIX](../../extensibility/internals/media/vsix-color-editor-hero.png "Immagine principale dell'editor dei colori VSIX")  
  
 **File di definizione del pacchetto**  
  
 I file di definizione del pacchetto (con estensione pkgdef) sono i file che definiscono i temi. I colori stessi vengono archiviati nei file color. XML del tema, che vengono compilati in un file con estensione pkgdef. I file con estensione pkgdef vengono distribuiti in percorsi ricercabili di Visual Studio, elaborati in fase di esecuzione e Uniti per definire i temi.  
  
 **Token di colore**  
  
 Un token di colore è costituito da quattro elementi:  
  
- **Nome categoria:** Raggruppamento logico per un set di colori. Usare un nome di categoria esistente se sono già presenti colori specifici per l'elemento dell'interfaccia utente desiderato o per il gruppo di elementi dell'interfaccia utente.  
  
- **Nome token:** Nome descrittivo per il token di colore e i set di token. I set includono i nomi di token in background e in primo piano (testo), così come tutti gli Stati, che devono essere denominati in modo da identificare facilmente le coppie e gli Stati a cui si applicano.  
  
- **Valori di colore (o tonalità):** Necessario per ogni tema colorato. Creare sempre valori di colore di sfondo e testo in coppie. I colori sono abbinati per sfondo/primo piano, in modo che il colore del testo (in primo piano) sia sempre leggibile rispetto al colore di sfondo in cui viene disegnato. Questi colori sono collegati e verranno usati insieme nell'interfaccia utente. Se lo sfondo non è destinato all'uso con testo, non definire un colore di primo piano.  
  
- **Nome colore sistema:** Da usare nelle visualizzazioni a contrasto elevato.  
  
## <a name="how-to-use-the-tool"></a>Come utilizzare lo strumento  
 Per quanto possibile, e laddove appropriato, è necessario riutilizzare i colori di Visual Studio esistenti anziché creare nuovi colori. Tuttavia, per i casi in cui non sono definiti colori appropriati, è necessario creare colori personalizzati per tenere compatibili i temi di estensione.  
  
 **Creazione di nuovi token di colore**  
  
 Per creare colori personalizzati usando l'Editor colori dell'estensione di Visual Studio, seguire questa procedura:  
  
1. Determinare la categoria e i nomi di token per i nuovi token di colore.  
  
2. Scegliere le tonalità che l'elemento dell'interfaccia utente utilizzerà per ogni tema e il colore di sistema per Contrasto elevato.  
  
3. Utilizzare l'Editor colori per creare nuovi token di colore.  
  
4. Usare i colori in un'estensione di Visual Studio.  
  
5. Testare le modifiche in Visual Studio.  
  
   **Passaggio 1: determinare la categoria e i nomi di token per i nuovi token di colore.**  
  
   Lo schema di denominazione preferito per un VSColor è **[Category] [tipo di interfaccia utente] [stato]** . Non usare la parola "color" nei nomi VSColor, perché è ridondante.  
  
   I nomi di categoria forniscono raggruppamenti logici e devono essere definiti nel modo più restrittivo possibile. Ad esempio, il nome di una singola finestra degli strumenti può essere un nome di categoria, ma il nome di un'intera business unit o del team di progetto non lo è. Il raggruppamento di voci in categorie consente di evitare confusione tra i colori con lo stesso nome.  
  
   Un nome di token deve indicare chiaramente il tipo di elemento e le situazioni, o "stato", per cui verrà applicato il colore. Un suggerimento per i dati attivi, ad **esempio, può essere** denominato "**DataTip**" e **[state]** potrebbe essere denominato "**Active**", ottenendo un nome di colore "**DataTipActive**". Poiché i suggerimenti dati hanno testo, è necessario definire sia un colore di primo piano che uno di sfondo. Utilizzando un'associazione in background o in primo piano, l'Editor colori creerà automaticamente i colori "**DataTipActive**" per lo sfondo e "**DataTipActiveText**" per il primo piano.  
  
   Se il componente dell'interfaccia utente dispone di un solo stato, è possibile omettere la parte **[state]** del nome. Se, ad esempio, una casella di ricerca dispone di un bordo e non vi sono modifiche di stato che potrebbero influire sul colore del bordo, il nome del token di colore del bordo può essere semplicemente chiamato "**SearchBoxBorder**".  
  
   Alcuni nomi di stato comuni includono:  
  
- Attivo  
  
- Inactive  
  
- MouseOver  
  
- MouseDown  
  
- Selected  
  
- Con stato attivo  
  
  Esempi di nomi di token per parti di un controllo elemento elenco:  
  
- ListItem  
  
- ListItemBorder  
  
- ListItemMouseOver  
  
- ListItemMouseOverBorder  
  
- ListItemSelected  
  
- ListItemSelectedBorder  
  
- ListItemDisabled  
  
- ListItemDisabledBorder  
  
  **Passaggio 2: scegliere le tonalità che l'elemento dell'interfaccia utente userà per ogni tema e il colore di sistema per Contrasto elevato.**  
  
  Quando si scelgono i colori personalizzati per l'interfaccia utente, selezionare un elemento dell'interfaccia utente esistente simile e utilizzarne i colori come base. I colori per gli elementi dell'interfaccia utente nella casella sono stati sottoposti a verifica e test, pertanto saranno appropriati e si comporteranno correttamente in tutti i temi.  
  
  **Passaggio 3: usare l'editor dei colori per creare nuovi token di colore.**  
  
  Avviare l'editor dei colori e aprire o creare un nuovo file con estensione XML del tema personalizzato. Selezionare **modifica > nuovo colore** dal menu. Verrà visualizzata una finestra di dialogo per specificare la categoria e uno o più nomi per le voci di colore all'interno di tale categoria:  
  
  ![Nuovo colore dell'Editor colori VSIX](../../extensibility/internals/media/vsix-color-editor-new-color.png "Nuovo colore dell'editor dei colori VSIX")  
  
  Selezionare una categoria esistente oppure selezionare **nuova categoria** per creare una nuova categoria. Si aprirà un'altra finestra di dialogo, creando un nuovo nome di categoria:  
  
  ![Nuova categoria dell'Editor colori VSIX](../../extensibility/internals/media/vsix-color-editor-new-category.png "Nuova categoria dell'editor dei colori VSIX")  
  
  La nuova categoria diventerà disponibile nel menu a discesa **nuova categoria colori** . Dopo aver scelto una categoria, immettere un nome per riga per ogni nuovo token di colore e selezionare "Crea" al termine:  
  
  ![Editor colori VSIX nuovo colore riempito](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "Nuovo colore riempito dell'editor dei colori VSIX")  
  
  I valori dei colori sono visualizzati nelle coppie sfondo/primo piano, con "None" che indica che il colore non è stato definito. Nota: se un colore non dispone di una coppia colore/sfondo colore testo, è necessario definire solo lo sfondo.  
  
  ![Valori dei colori dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "Valori di colore dell'editor dei colori VSIX")  
  
  Per modificare un token di colore, selezionare una voce di colore per il tema (colonna) del token. Aggiungere il valore del colore digitando un valore di colore esadecimale in formato ARGB a 8 cifre, immettendo un nome di colore di sistema nella cella o usando il menu a discesa per selezionare il colore desiderato tramite un set di dispositivi di scorrimento dei colori o un elenco di colori di sistema.  
  
  ![Colore di modifica dell'Editor colori VSIX](../../extensibility/internals/media/vsix-color-editor-edit-color.png "Modifica del colore dell'editor dei colori VSIX")  
  
  ![Sfondo dell'Editor colori VSIX](../../extensibility/internals/media/vsix-color-editor-background.png "Sfondo dell'editor dei colori VSIX")  
  
  Per i componenti che non devono visualizzare il testo, immettere un solo valore di colore: il colore di sfondo. In caso contrario, immettere i valori per lo sfondo e il colore del testo, separati da una barra.  
  
  Quando si immettono valori per Contrasto elevato, immettere nomi dei colori di sistema Windows validi. Non immettere valori ARGB hardcoded. È possibile visualizzare un elenco di nomi di colori del sistema validi selezionando "background: System" o "Foreground: System" nei menu a discesa dei valori di colore. Quando si creano elementi con componenti di testo, usare la coppia di colori di sistema in background/text corretta oppure il testo potrebbe essere illeggibile.  
  
  Al termine della creazione, dell'impostazione e della modifica dei token di colore, salvarli nel formato XML o pkgdef desiderato. I token di colore, né uno sfondo né un set di primo piano, verranno salvati come colori vuoti in formato XML, ma eliminati nel formato. pkgdef. Se si tenta di salvare i colori vuoti in un file con estensione pkgdef, verrà visualizzata una finestra di dialogo che segnala la potenziale perdita di colore.  
  
  **Passaggio 4: usare i colori in un'estensione di Visual Studio.**  
  
  Dopo aver definito i nuovi token di colore, includere il file con estensione pkgdef nel file di progetto con "azione di compilazione" impostata su "contenuto" e "Includi in VSIX" impostato su "true".  
  
  ![Editor colori VSIX pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "File pkgdef dell'editor dei colori VSIX")  
  
  Nell'Editor colori dell'estensione di Visual Studio scegliere File > Visualizza codice risorsa per visualizzare il codice usato per accedere ai colori personalizzati nell'interfaccia utente basata su WPF.  
  
  ![Visualizzatore codice risorse Editor colori VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "Visualizzatore del codice delle risorse dell'editor dei colori VSIX")  
  
  Includere questo codice in una classe statica nel progetto. Per utilizzare il tipo **ThemeResourceKey** , è necessario aggiungere al progetto un riferimento a **Microsoft. VisualStudio. Shell.\<VSVersion >. 0. dll** .  
  
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
  
 Questo consente l'accesso ai colori nel codice XAML e consente all'interfaccia utente di rispondere alle modifiche del tema.  
  
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
  
 **Passaggio 5: testare le modifiche in Visual Studio.**  
  
 L'editor dei colori può applicare temporaneamente i token dei colori alle istanze in esecuzione di Visual Studio per visualizzare le modifiche in tempo reale ai colori senza ricompilare il pacchetto di estensione. A tale scopo, fare clic sul pulsante "applica questo tema all'esecuzione di Visual Studio Windows" posizionato nell'intestazione di ogni colonna del tema. Questo tema temporaneo scomparirà al termine della chiusura dell'editor dei colori VSIX.  
  
 ![Applicazione dell'Editor colori VSIX](../../extensibility/internals/media/vsix-color-editor-apply.png "Applicazione dell'editor dei colori VSIX")  
  
 Per rendere permanenti le modifiche, ricompilare e ridistribuire l'estensione di Visual Studio dopo aver aggiunto i nuovi colori al file con estensione pkgdef e scrivendo il codice che utilizzerà tali colori. Ricompilando l'estensione di Visual Studio, i valori del registro di sistema per i nuovi colori vengono uniti nel resto dei temi. Quindi riavviare Visual Studio, visualizzare l'interfaccia utente e verificare che i nuovi colori siano visualizzati come previsto.  
  
## <a name="notes"></a>Note  
 Questo strumento può essere usato per creare colori personalizzati per i temi di Visual Studio preesistenti o per modificare i colori di un tema di Visual Studio personalizzato. Per creare temi personalizzati completi di Visual Studio, scaricare l' [estensione Visual Studio color Theme Editor](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) dalla raccolta estensioni di Visual Studio.  
  
## <a name="sample-output"></a>Output di esempio  
 **Output del colore XML**  
  
 Il file XML generato dallo strumento sarà simile al seguente:  
  
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
  
 **Output colore PKGDEF**  
  
 Il file. pkgdef generato dallo strumento sarà simile al seguente:  
  
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
  
 **C#wrapper di chiavi di risorsa**  
  
 Le chiavi di risorsa di colore generate dallo strumento saranno simili alle seguenti:  
  
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
  
 Le chiavi di colore **ResourceDictionary** generate dallo strumento saranno simili alle seguenti:  
  
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
