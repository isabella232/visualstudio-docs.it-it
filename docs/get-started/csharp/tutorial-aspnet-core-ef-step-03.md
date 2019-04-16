---
title: "Passaggio 3: Uso dei dati nell'app ASP.NET Core"
description: Iniziare a usare i dati con Entity Framework Core nell'app Web ASP.NET Core con questa esercitazione video e istruzioni dettagliate.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: c1d95d7621a97a36fdf737e7d3dd4f8baf713645
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018181"
---
# <a name="step-3-work-with-data-using-entity-framework"></a>Passaggio 3: Usare i dati con Entity Framework

Seguire questi passaggi per iniziare a usare i dati con Entity Framework Core nell'app Web ASP.NET Core.

_Guardare questo video e seguire le indicazioni per aggiungere dati alla prima app ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/dulJCwNrqhM]

## <a name="open-your-project"></a>Aprire il progetto

Se si stanno eseguendo queste esercitazioni video in sequenza, aprire il progetto di applicazione Web creato nella sezione precedente. Se si inizia da qui, è necessario creare un nuovo progetto e scegliere **Applicazione Web ASP.NET** e quindi **Applicazione Web**. Per le altre opzioni lasciare invariate le impostazioni predefinite.

## <a name="add-your-model"></a>Aggiungere il modello

La prima operazione da eseguire per usare i dati nell'applicazione ASP.NET Core è descrivere l'aspetto dei dati. Questa operazione viene definita creazione di un *modello* degli aspetti coinvolti nel problema che si sta cercando di risolvere. Nelle applicazioni reali sarà necessario aggiungere logica di business personalizzata a questi modelli in modo che possano offrire comportamenti specifici e automatizzare le attività. Per questo esempio, verrà creato un sistema semplice per tenere traccia di giochi da tavolo. È necessaria una classe che rappresenta un gioco e include alcune proprietà che potrebbe essere necessario registrare per il gioco, come il numero di giocatori supportati. La classe verrà inserita in una nuova cartella che verrà creata nella radice del progetto Web, denominata *Modelli*.

```csharp
public class Game
{
    public int Id { get; set; }
    public string Title { get; set; }
    public int PublicationYear { get; set; }
    public int MinimumPlayers { get; set; }
    public int MaximumPlayers { get; set; }
}
```

## <a name="create-the-pages-to-manage-your-game-library"></a>Creare le pagine per gestire la libreria di giochi

A questo punto è possibile procedere con la creazione delle pagine che verranno usate per gestire la libreria di giochi. Nonostante quello che si potrebbe immaginare, l'operazione è in effetti incredibilmente semplice. Prima di tutto è necessario decidere dove posizionare questa funzionalità nell'app. Aprire la cartella Pagine nel progetto Web e aggiungere una nuova cartella. Chiamarla *Games*.

Fare ora clic con il pulsante destro del mouse sulla cartella Games e scegliere **Aggiungi** > **Nuovo elemento di scaffolding**. Scegliere l'opzione **Pagine Razor che usano Entity Framework (CRUD)**. CRUD è l'acronimo d"Create, Read, Update, Delete" (Creare, leggere, aggiornare, eliminare) e questo modello creerà le pagine per ogni operazione (incluse una pagina per elencare tutti gli elementi e una pagina per visualizzare i dettagli di un elemento).

![ASP.NET Core di Visual Studio 2019 - Aggiungere pagine con scaffolding](media/vs-2019/vs2019-add-scaffold.png)

Selezionare la classe modello di gioco e usare l'icona '+' per aggiungere una nuova classe contesto dati. Assegnargli il nome `AppDbContext`. Lasciare le altre impostazioni predefinite e fare clic su **Aggiungi**.

Nella cartella Games verranno aggiunte le pagine Razor seguenti:

- Create.cshtml
- Delete.cshtml
- Details.cshtml
- Edit.cshtml
- Index.cshtml

![ASP.NET Core di Visual Studio 2019 - Pagine con scaffolding](media/vs-2019/vs2019-scaffolded-pages.png)

Oltre ad aggiungere pagine nella cartella *Games*, l'operazione di scaffolding ha aggiunto codice nella classe *Startup.cs*. Esaminando il metodo `ConfigureServices` in questa classe si noterà che è stato aggiunto questo codice:

```csharp
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("AppDbContext")));
```

Si noterà anche che è stata aggiunta la stringa di connessione `AppDbContext` al file *appsettings.json* del progetto.

Se si esegue l'app a questo punto, potrebbe verificarsi un errore perché non è ancora stato creato un database. È possibile configurare l'app per la creazione automatica del database se richiesto, [aggiungendo codice al file Program.cs](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio#update-main):

```csharp
public static void Main(string[] args)
{
    var host = CreateWebHostBuilder(args).Build();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        try
        {
            var context = services.GetRequiredService<SchoolContext>();
            context.Database.EnsureCreated();
        }
        catch (Exception ex)
        {
            var logger = services.GetRequiredService<ILogger<Program>>();
            logger.LogError(ex, "An error occurred creating the DB.");
        }
    }

    host.Run();
}
```

La maggior parte del codice è destinata semplicemente alla gestione degli errori e per consentire l'accesso ad `AppDbContext` di EF Core prima dell'esecuzione dell'app. La riga importante è quella con `context.Database.EnsureCreated()`, che creerà il database se non esiste già. A questo punto l'app è pronta per l'esecuzione.

## <a name="test-it-out"></a>Testare l'app

Eseguire l'applicazione e passare a `/Games` nella barra degli indirizzi. Verrà visualizzata una pagina con un elenco vuoto. Fare clic su **Create New** (Crea nuovo) per aggiungere un nuovo elemento `Game` alla raccolta. Compilare il modulo e fare clic su **Create** (Crea). Il gioco dovrebbe comparire nella visualizzazione elenco. Fare clic su **Details** (Dettagli) per visualizzare i dettagli di un singolo record.

Aggiungere un altro record. È possibile fare clic su *Edit* (Modifica) per modificare i dettagli di un record, o su **Delete** (Elimina) per rimuoverlo. In questo caso verrà richiesta conferma prima dell'effettiva eliminazione del record.

![ASP.NET Core di Visual Studio 2019 - Pagine con scaffolding nel browser](media/vs-2019/vs2019-game-list.png)

Questo è tutto per iniziare a usare i dati in un'app ASP.NET Core con EF Core e Visual Studio 2019.

## <a name="next-steps"></a>Passaggi successivi

Nel prossimo video si apprenderà come aggiungere il supporto dell'API Web per l'app.

[Passaggio 4: Esposizione di un'API Web dall'app ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)

## <a name="see-also"></a>Vedere anche

- [Razor Pages con Entity Framework Core in ASP.NET Core](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio)
- [ASP.NET Core Razor Pages con Entity Framework Core](/aspnet/core/data/?view=aspnetcore-2.1)
