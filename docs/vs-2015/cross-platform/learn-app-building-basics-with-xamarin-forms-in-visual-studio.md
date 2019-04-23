---
title: Nozioni di base della creazione di app con xamarin. Forms
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: add48cc007b9108e565ae89d987caf2797b897f0
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664637"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Nozioni di base sulla compilazione di app con Xamarin.Forms in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dopo aver eseguito i passaggi [Setup and install](../cross-platform/setup-and-install.md) e [Verify your Xamarin environment](../cross-platform/verify-your-xamarin-environment.md), questa procedura dettagliata illustra come compilare un'app di base (mostrata sotto) con Xamarin.Forms. Con Xamarin.Forms tutto il codice dell'interfaccia utente viene scritto una sola volta in una libreria di classi portabile (PCL). Xamarin esegue quindi il rendering automatico dei controlli dell'interfaccia utente nativi per le piattaforme iOS, Android e Windows. Questo approccio è consigliato perché l'opzione PCL funziona meglio se si usano solo le API .NET supportate in tutte le piattaforme di destinazione e perché Xamarin.Forms consente di condividere il codice dell'interfaccia utente tra le piattaforme.

 ![Esempio di app Meteo per Android, iOS e Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

 Verranno eseguite queste operazioni per la creazione dell'app:

-   [Configurare la soluzione](#solution)

-   [Scrivere un codice di servizio dati condiviso](#dataservice)

-   [Iniziare a scrivere il codice dell'interfaccia utente condiviso](#uicode)

-   [Testare l'app usando Visual Studio Emulator for Android](#test)

-   [Terminare l'interfaccia utente con un aspetto nativo tra le piattaforme](#finish)

> [!TIP]
>  È possibile trovare il codice sorgente completo per questo progetto nella finestra di [archivio degli esempi di Xamarin-Forms in GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).

##  <a name="solution"></a> Configurare la soluzione
 Questi passaggi consentono di creare una soluzione Xamarin.Forms che contiene una libreria di classi portabile (PCL) per il codice condiviso e due pacchetti NuGet aggiunti.

1.  In Visual Studio creare una nuova soluzione **Applicazione vuota (Xamarin.Forms portabile)** e denominarla **WeatherApp**. Il modello può essere individuato più facilmente immettendo **Xamarin.Forms** nel campo di ricerca.

     Se non è presente, potrebbe essere necessario installare Xamarin o abilitare la funzionalità di Visual Studio 2015. Vedere [Configurazione e installazione](../cross-platform/setup-and-install.md).

     ![Creazione di un nuovo progetto App vuota &#40;Xamarin.Forms portatile&#41;](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2.  Dopo aver fatto clic su OK per creare la soluzione vengono visualizzati diversi progetti singoli:

    -   **WeatherApp (portabile)**: la libreria di classi portabile (PCL) in cui verrà scritto il codice condiviso tra le piattaforme, inclusa la logica di business comune e il codice dell'interfaccia utente in uso con Xamarin.Forms.

    -   **WeatherApp.Droid**: il progetto che contiene il codice Android nativo. Viene impostato come progetto di avvio predefinito.

    -   **WeatherApp.iOS**: il progetto che contiene il codice iOS nativo.

    -   **WeatherApp.UWP**: progetto che contiene il codice UWP di Windows 10.

    -   **WeatherApp.Windows (Windows 8.1)**: progetto che contiene il codice nativo di Windows 8.1.

    -   **WeatherApp.WinPhone (Windows Phone 8.1)**: progetto che contiene il codice nativo di Windows Phone.

    > [!NOTE]
    >  È possibile eliminare qualsiasi progetto presente in piattaforme a cui non si fa riferimento. Ai fini di questa procedura dettagliata, si farà riferimento ai progetti Windows Phone 8.1, iOS e Android. L'uso di progetti Windows 8.1 e UWP è molto simile a quello di progetti Windows Phone 8.1.

     In ogni progetto nativo si ha accesso alla finestra di progettazione nativa per la piattaforma corrispondente e si possono implementare schermate e funzionalità specifiche della piattaforma secondo necessità.

3.  Aggiornare il pacchetto NuGet di Xamarin.Forms nella soluzione all'ultima versione stabile come descritto di seguito. Si consiglia di eseguire questa operazione ogni volta che si crea una nuova soluzione Xamarin:

    -   Selezionare **Strumenti > Gestione pacchetti NuGet > Gestisci pacchetti NuGet per la soluzione**.

    -   Nella scheda **Aggiornamenti** scegliere l'aggiornamento **Xamarin.Forms** e selezionare l'aggiornamento di tutti i progetti nella soluzione. Nota: lasciare deselezionati gli aggiornamenti per Xamarin.Android.Support.

    -   Aggiornare il campo **Versione** all' **Ultima versione stabile** disponibile.

    -   Fare clic su **Aggiorna**.

         ![Aggiornamento del pacchetto NuGet di Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")

4.  Aggiungere il pacchetto NuGet e **Newtonsoft.Json** al progetto PCL, che verranno usati per elaborare le informazioni recuperate da un servizio di dati meteo:

    -   In Gestione pacchetti NuGet (aperto nel passaggio 3) selezionare la scheda **Sfoglia** e cercare **Newtonsoft**.

    -   Selezionare **Newtonsoft.Json**.

    -   Selezionare il progetto **WeatherApp** , che rappresenta l'unico progetto in cui è necessario installare il pacchetto.

    -   Verificare che il campo **Versione** sia impostato su **Ultima versione stabile** .

    -   Fare clic su **Installa**.

    -   ![Individuare e installare il pacchetto NuGet Newtonsoft.Json](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

5.  Ripetere il passaggio 4 per trovare e installare il pacchetto **Microsoft.Net.Http** .

6.  Compilare la soluzione e verificare che non ci siano errori di compilazione.

##  <a name="dataservice"></a> Scrivere un codice di servizio dati condiviso
 **WeatherApp (portabile)** è il progetto di destinazione del codice per la libreria di classi portabile (PCL) condiviso tra le piattaforme. La libreria di classi portabile (PCL) viene inclusa automaticamente nei pacchetti di app compilati dai progetti iOS, Android e Windows Phone.

 Per eseguire questo esempio, è prima di tutto necessario iscriversi per una chiave API gratuita all'indirizzo [http://openweathermap.org/appid](http://openweathermap.org/appid).

 I passaggi seguenti aggiungono il codice alla libreria di classi portabile (PCL) per accedere e archiviare i dati dal servizio meteo:

1.  Fare clic con il pulsante destro del mouse sul progetto **WeatherApp** e selezionare **Aggiungi > Classe**. Nella finestra di dialogo **Aggiungi nuovo elemento** denominare il file **Weather.cs**. Questa classe verrà usata per archiviare i dati dal servizio di dati meteo.

2.  Sostituire tutto il contenuto di **Weather.cs** con:

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            public string Title { get; set; }
            public string Temperature { get; set; }
            public string Wind { get; set; }
            public string Humidity { get; set; }
            public string Visibility { get; set; }
            public string Sunrise { get; set; }
            public string Sunset { get; set; }

            public Weather()
            {
                //Because labels bind to these values, set them to an empty string to
                //ensure that the label appears on all platforms by default.
                this.Title = " ";
                this.Temperature = " ";
                this.Wind = " ";
                this.Humidity = " ";
                this.Visibility = " ";
                this.Sunrise = " ";
                this.Sunset = " ";
            }
        }
    }
    ```

3.  Aggiungere un'altra classe al progetto PCL denominato **DataService.cs** usato per elaborare i dati JSON dal servizio di dati meteo.

4.  Sostituire tutto il contenuto di **DataService.cs** con il codice seguente:

    ```csharp
    using System.Threading.Tasks;
    using Newtonsoft.Json;
    using System.Net.Http;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> getDataFromService(string queryString)
            {
                HttpClient client = new HttpClient();
                var response = await client.GetAsync(queryString);

                dynamic data = null;
                if (response != null)
                {
                    string json = response.Content.ReadAsStringAsync().Result;
                    data = JsonConvert.DeserializeObject(json);
                }

                return data;
            }
        }
    }
    ```

5.  Aggiungere una terza classe alla libreria di classi portabile (PCL) denominata **Core** in cui inserire la logica di business condivisa, ad esempio una logica che forma una stringa di query usando un codice postale, chiama il servizio di dati meteo, quindi popola un'istanza della classe **Weather** .

6.  Sostituire il contenuto di **Core.cs** con:

    ```csharp
    using System;
    using System.Threading.Tasks;

    namespace WeatherApp
    {
        public class Core
        {
            public static async Task<Weather> GetWeather(string zipCode)
            {
                //Sign up for a free API key at http://openweathermap.org/appid
                string key = "YOUR KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);

                if (results["weather"] != null)
                {
                    Weather weather = new Weather();
                    weather.Title = (string)results["name"];
                    weather.Temperature = (string)results["main"]["temp"] + " F";
                    weather.Wind = (string)results["wind"]["speed"] + " mph";
                    weather.Humidity = (string)results["main"]["humidity"] + " %";
                    weather.Visibility = (string)results["weather"][0]["main"];

                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);
                    weather.Sunrise = sunrise.ToString() + " UTC";
                    weather.Sunset = sunset.ToString() + " UTC";
                    return weather;
                }
                else
                {
                    return null;
                }
            }
        }
    }
    ```

7.  Compilare il progetto PCL **WeatherApp** per verificare che il codice sia corretto.

##  <a name="uicode"></a> Iniziare a scrivere il codice dell'interfaccia utente condiviso
 Xamarin.Forms consente di implementare il codice dell'interfaccia utente condiviso nella libreria di classi portabile (PCL). In questi passaggi verrà aggiunta una schermata alla libreria di classi portabile (PCL) con un pulsante che aggiorna il testo con i dati restituiti dal codice del servizio di dati meteo aggiunto nella sezione precedente:

1.  Aggiungere una **pagina XAML Form** denominata **WeatherPage.cs** facendo clic con il pulsante destro del mouse sul progetto **WeatherApp** e selezionando **Aggiungi > Nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** cercare "Form", selezionare la **pagina XAML Form**, quindi denominarla **WeatherPage.cs**.

     Xamarin.Forms è basato su XAML, quindi questo passaggio crea un file **WeatherPage.xaml** e un file code-behind annidato **WeatherPage.xaml.cs**. Ciò consente di generare l'interfaccia utente tramite XAML o il codice. In questa procedura dettagliata verranno eseguite operazioni relative a entrambi i casi.

     ![Aggiunta di una nuova pagina XAML Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")

2.  Per aggiungere un pulsante alla schermata WeatherPage, sostituire i contenuti di WeatherPage.xaml con:

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage">
      <Button x:Name="getWeatherBtn" Text="Get Weather"/>
    </ContentPage>
    ```

     Il nome del pulsante deve essere definito usando l'attributo **x:Name** , in modo che si possa fare riferimento al pulsante tramite il nome all'interno del file code-behind.

3.  Per aggiungere un gestore eventi per l'evento **Selezionato** del pulsante per aggiornarne il testo, sostituire i contenuti di **WeatherPage.xaml.cs** con il codice seguente. Il codice postale "60601" può essere liberamente modificato.

    ```csharp
    using System;
    using Xamarin.Forms;

    namespace WeatherApp
    {
        public partial class WeatherPage: ContentPage
        {
            public WeatherPage()
            {
                InitializeComponent();
                this.Title = "Sample Weather App";
                getWeatherBtn.Clicked += GetWeatherBtn_Clicked;

                //Set the default binding to a default object for now
                this.BindingContext = new Weather();
            }

            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
            {
                Weather weather = await Core.GetWeather("60601");
                getWeatherBtn.Text = weather.Title;
            }
        }
    }
    ```

4.  Per aprire **WeatherPage** come prima schermata quando viene avviata l'app, sostituire il costruttore predefinito in **App.cs** con il codice seguente:

    ```csharp
    public App()
    {
        MainPage = new NavigationPage(new WeatherPage());
    }
    ```

5.  Compilare il progetto PCL WeatherApp per verificare che il codice sia corretto.

##  <a name="test"></a> Testare l'app usando Visual Studio Emulator for Android
 È ora possibile eseguire l'app. Eseguire, per ora, solo la versione Android per verificare che l'app stia ottenendo i dati dal servizio meteo. In un secondo momento verranno eseguite anche le versioni di Windows Phone e iOS dopo aver aggiunto altri elementi dell'interfaccia utente. Nota: se si esegue Visual Studio in Windows 7, la procedura resta la stessa ma verrà usato Xamarin Player.

1.  Impostare il progetto **WeatherApp.Droid** come progetto di avvio facendo clic con il pulsante destro del mouse su di esso e selezionando **Imposta come progetto di avvio**.

2.  Nella barra degli strumenti di Visual Studio viene visualizzato **WeatherApp.Droid** come progetto di destinazione. Selezionare uno degli emulatori di Android per il debug e premere **F5**. Si consiglia di usare una delle opzioni di **VS Emulator** , che eseguirà l'app in Visual Studio Emulator per le opzioni Android.

     ![Selezione di una destinazione di debug di VS Emulator](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

3.  Quando l'app viene avviata nell'emulatore, fare clic sul pulsante **Get Weather** . Verrà aggiornato il testo del pulsante a **Chicago, IL**, che è la proprietà *Title* dei dati recuperati dal servizio meteo.

     ![App Meteo prima e dopo un tocco sul pulsante](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")

##  <a name="finish"></a> Terminare l'interfaccia utente con un aspetto nativo tra le piattaforme
 Xamarin.Forms esegue il rendering dei controlli dell'interfaccia utente nativi per ciascuna piattaforma, in modo da conferire un aspetto nativo all'app. Per maggiore chiarezza, completare l'interfaccia utente con un campo di input per il codice postale, quindi visualizzare i dati meteo restituiti dal servizio.

1. Sostituire il contenuto di **WeatherPage.xaml** con il codice seguente. Ogni elemento viene denominato usando l'attributo **x:Name** come descritto in precedenza, in modo che si possa fare riferimento all'elemento dal codice. Xamarin.Forms fornisce anche diverse [opzioni di layout](http://developer.xamarin.com/guides/xamarin-forms/controls/layouts/) (xamarin.com). In questo caso, WeatherPage usa [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/) (xamarin.com).

   ```xaml
   <?xml version="1.0" encoding="utf-8" ?>
   <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
          xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
          x:Class="WeatherApp.WeatherPage">

     <ContentPage.Resources>
       <ResourceDictionary>
         <Style x:Key="labelStyle" TargetType="Label">
           <Setter Property="TextColor" Value="#a8a8a8" />
           <Setter Property="FontSize" Value="Small" />
         </Style>
         <Style x:Key="fieldStyle" TargetType="Label">
           <Setter Property="TextColor">
             <OnPlatform x:TypeArguments="Color" iOS="Black" Android="White" WinPhone="White" />
           </Setter>
           <Setter Property="FontSize" Value="Medium" />
         </Style>
         <Style x:Key="fieldView" TargetType="ContentView">
           <Setter Property="Padding" Value="10,0,0,0" />
         </Style>
       </ResourceDictionary>
     </ContentPage.Resources>

     <ContentPage.Content>
       <ScrollView>
         <StackLayout>
           <StackLayout Orientation="Horizontal" HorizontalOptions="FillAndExpand"
                 BackgroundColor="#545454">
             <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
               <Label Text="Search by Zip Code" TextColor="White" FontAttributes="Bold"
                   FontSize="Medium" />
               <Label x:Name="zipCodeLabel" Text="Zip Code" Style="{StaticResource labelStyle}" />
               <Entry x:Name="zipCodeEntry" />
             </StackLayout>
             <StackLayout Padding="0,0,0,10" VerticalOptions="End">
               <Button x:Name="getWeatherBtn" Text="Get Weather" WidthRequest="185" BorderWidth="1" >
                 <!-- Set iOS colors; use defaults on other platforms -->
                 <Button.TextColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.TextColor>
                 <Button.BorderColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.BorderColor>
               </Button>
             </StackLayout>
           </StackLayout>
           <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
             <Label Text="Location" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Temperature" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="tempLabel" Text="{Binding Temperature}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="windLabel" Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Humidity" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="humidityLabel" Text="{Binding Humidity}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Visibility" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="visibilitylabel" Text="{Binding Visibility}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunriseLabel" Text="{Binding Sunrise}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunsetLabel" Text="{Binding Sunset}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
           </StackLayout>
         </StackLayout>
       </ScrollView>
     </ContentPage.Content>
   </ContentPage>
   ```

    Si noti l'uso del tag **OnPlatform** in Xamarin.Forms. Il tag**OnPlatform** seleziona un valore della proprietà specifico per la piattaforma corrente in cui è in esecuzione l'app (vedere la sezione relativa alla [sintassi XAML esterna](http://developer.xamarin.com/guides/xamarin-forms/user-interface/xaml-basics/essential_xaml_syntax/) (xamarin.com). Qui usiamo per impostare un colore del testo diversi per i campi dati: Bianco in Android e Windows Phone, nero in iOS. **OnPlatform** può essere usato per qualsiasi proprietà e tipo di dati per apportare modifiche specifiche per la piattaforma in qualsiasi punto del file XAML. Nel file code-behind è possibile usare [Device.OnPlatform API](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) per lo stesso scopo.

2. In **WeatherPage.xaml.cs**sostituire il gestore eventi **GetWeatherBtn_Clicked** con il codice seguente. Questo codice verifica che sia presente un codice postale nel campo di immissione, recupera i dati da tale codice, imposta il contesto di associazione dell'intera schermata sull'istanza Weather risultante, quindi imposta il testo del pulsante su "Cerca di nuovo". Ogni etichetta nell'interfaccia utente viene associata a una proprietà della classe Weather, quindi, quando si imposta il contesto di associazione della schermata su un'istanza **Weather** , le etichette vengono aggiornate automaticamente.

   ```csharp
   private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
   {
       if (!String.IsNullOrEmpty(zipCodeEntry.Text))
       {
           Weather weather = await Core.GetWeather(zipCodeEntry.Text);
           this.BindingContext = weather;
           getWeatherBtn.Text = "Search Again";
       }
   }
   ```

3. Eseguire l'app in tutte e tre le piattaforme, Android, iOS e Windows Phone, facendo clic con il pulsante destro del mouse sul progetto appropriato, selezionando Imposta come progetto di avvio e avviando l'app in un dispositivo o in un emulatore o simulatore. Immettere un codice postale degli Stati Uniti valido, ad esempio 60601, e premere il pulsante Get Weather per visualizzare i dati meteo per l'area, come mostrato di seguito. Ovviamente, Visual Studio deve essere connesso a un computer Mac OS X nella rete per il progetto iOS.

    ![Esempio di app Meteo per Android, iOS e Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

   Il codice sorgente completo per questo progetto si trova in [archivio degli esempi di Xamarin-Forms in GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).
