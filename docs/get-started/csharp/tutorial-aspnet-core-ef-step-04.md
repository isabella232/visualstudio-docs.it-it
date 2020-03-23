---
title: "Passaggio 4: Esposizione di un'API Web dall'app ASP.NET coreStep 4: Exposing a web API From Your ASP.NET Core App"
description: Aggiungere un'API Web all'app Web ASP.NET Core con questa esercitazione video e le istruzioni dettagliate.
ms.custom: get-started
ms.date: 02/13/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 5ea9468bdf86986ab542fb1cabc873c9aeb75fd6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580045"
---
# <a name="step-4-expose-a-web-api-from-your-aspnet-core-app"></a>Passaggio 4: Esporre un'API Web dall'app ASP.NET CoreStep 4: Expose a web API from your ASP.NET Core app

Seguire questa procedura per aggiungere un'API Web a un'app ASP.NET Core esistente.

_Guardare questo video e seguire le indicazioni per aggiungere il supporto di un'API Web alla prima app ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/o_fYPOsAXts]

## <a name="open-your-project"></a>Aprire il progetto

Aprire l'app ASP.NET Core in Visual Studio 2019. È necessario che l'app usi già EF Core per gestire i tipi di modello, come configurato nel [passaggio 3 di questa serie di esercitazioni](tutorial-aspnet-core-ef-step-03.md).

## <a name="add-an-api-controller"></a>Aggiungere un controller API

Fare clic con il pulsante destro del mouse sul progetto e aggiungere una nuova cartella denominata *Api*. Quindi, fare clic con il pulsante destro del mouse su questa cartella e scegliere **Aggiungi** > **nuovo elemento con scaffolding**. Scegliere **Controller API con azioni, che usa Entity Framework**. A questo punto, scegliere una classe modello esistente e fare clic su **Aggiungi**.

![Controller API di scaffolding di ASP.NET Core in Visual Studio 2019](media/vs-2019/vs2019-add-scaffold-api.png)

## <a name="reviewing-the-generated-controller"></a>Verifica del controller generato

Il codice generato include una nuova classe controller. Nella parte superiore della definizione della classe vi sono due attributi.

```csharp
[Route("api/[controller]")]
[ApiController]
public class GamesController : ControllerBase
```

Il primo specifica la route per le azioni in questo controller come `api/[controller]`, che significa che se il controller è denominato `GamesController` la route sarà `api/Games`.

Il secondo attributo `[ApiController]`, aggiunge alcune convalide utili alla classe, ad esempio garantire che ogni metodo di azione includa un proprio attributo `[Route]`.

```csharp
public class GamesController : ControllerBase
{
    private readonly AppDbContext _context;

    public GamesController(AppDbContext context)
    {
        _context = context;
    }
```

Il controller usa l'`AppDbContext` esistente, passato nel relativo costruttore. Ogni azione userà questo campo per operare sui dati dell'applicazione.

```csharp
// GET: api/Games
[HttpGet]
public IEnumerable<Game> GetGame()
{
    return _context.Game;
}
```

Il primo metodo è una semplice richiesta GET, come specificato con l'attributo `[HttpGet]`. Non accetta parametri e restituisce un elenco di tutti i giochi nel database.

```csharp
// GET: api/Games/5
[HttpGet("{id}")]
public async Task<IActionResult> GetGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);

    if (game == null)
    {
        return NotFound();
    }

    return Ok(game);
}
```

Il metodo successivo specifica `{id}` nella route, che verrà aggiunto alla ruote dopo una `/`, in modo che la route completa sarà simile a `api/Games/5` come illustrato nel commento nella parte superiore. Per l'input `id` viene eseguito il mapping al parametro `id` nel metodo. All'interno del metodo, se il modello non è valido, viene restituito un risultato `BadRequest`. In caso contrario, Entity Framework tenterà di trovare il record corrispondente all'`id` specificato. Se non riesce, viene restituito un risultato `NotFound`. In caso contrario, viene restituito il record `Game` appropriato.

```csharp
// PUT: api/Games/5
[HttpPut("{id}")]
public async Task<IActionResult> PutGame([FromRoute] int id, [FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    if (id != game.Id)
    {
        return BadRequest();
    }

    _context.Entry(game).State = EntityState.Modified;

    try
    {
        await _context.SaveChangesAsync();
    }
    catch (DbUpdateConcurrencyException)
    {
        if (!GameExists(id))
        {
            return NotFound();
        }
        else
        {
            throw;
        }
    }

    return NoContent();
}
```

Successivamente, viene usata una richiesta `[HttpPut]` all'API per eseguire gli aggiornamenti. Il nuovo record `Game` viene fornito nel corpo della richiesta. Vengono eseguiti alcuni controlli di convalida e degli errori. Se tutto risulta corretto, il record nel database viene aggiornato con i valori specificati nel corpo della richiesta. In caso contrario, viene restituita una risposta di errore appropriata.

```csharp
// POST: api/Games
[HttpPost]
public async Task<IActionResult> PostGame([FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    _context.Game.Add(game);
    await _context.SaveChangesAsync();

    return CreatedAtAction("GetGame", new { id = game.Id }, game);
}
```

Viene usata una richiesta `[HttpPost]` per aggiungere nuovi record nel sistema. Come con `[HttpPut]`, il record viene aggiunto nel corpo della richiesta. Se è valido, EF Core aggiunge il record al database e l'azione restituisce il record aggiornato (con l'ID generato dal database) e un collegamento al record nell'API.

```csharp
// DELETE: api/Games/5
[HttpDelete("{id}")]
public async Task<IActionResult> DeleteGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);
    if (game == null)
    {
        return NotFound();
    }

    _context.Game.Remove(game);
    await _context.SaveChangesAsync();

    return Ok(game);
}
```

Infine, viene usata una route `[HttpDelete]` con un ID per eliminare un record. Se la richiesta è valida ed esiste un record con l'ID specificato, EF Core lo elimina dal database.

## <a name="adding-swagger"></a>Aggiunta di Swagger

Swagger è uno strumento per il testing e la documentazione dell'API, che può essere aggiunto come un set di servizi e middleware a un'app ASP.NET Core. A tale scopo, fare clic con il pulsante destro del mouse sul progetto e scegliere **Gestisci pacchetti NuGet**. Quindi, **Browse**fare clic `Swashbuckle.AspNetCore`su Sfoglia , cercare e installare la versione 4.0.1.

![Visual Studio 2019 - Aggiunta di Swashbuckle da Nuget](media/vs-2019/vs2019-nuget-swashbuckle.png)

Una volta installato, aprire `Startup.cs` e aggiungere il codice seguente alla fine del metodo `ConfigureServices`:

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new Info { Title = "My API", Version = "v1" });
});
```

Sarà necessario anche aggiungere `using Swashbuckle.AspNetCore.Swagger;` nella parte superiore del file.

Aggiungere poi il codice seguente al metodo `Configure`, subito prima di `UseMvc`:

```csharp
// Enable middleware to serve generated Swagger as a JSON endpoint.
app.UseSwagger();

// Enable middleware to serve swagger-ui (HTML, JS, CSS, etc.), 
// specifying the Swagger JSON endpoint.
app.UseSwaggerUI(c =>
{
    c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
});
```

A questo punto dovrebbe essere possibile compilare ed eseguire l'app. Nel browser passare a `/swagger` nella barra degli indirizzi. Verrà visualizzato un elenco di endpoint e modelli dell'API dell'app. 

![Visual Studio 2019 - Pagina di Swagger nel browser](media/vs-2019/vs2019-swagger-browser.png)

Fare clic su un endpoint in Games e quindi su `Try it out` e `Execute` per vedere come si comportano i diversi endpoint.

## <a name="next-steps"></a>Passaggi successivi

Nel prossimo video verrà spiegato come distribuire l'app in Azure.

[Passaggio 5: Distribuzione dell'app di base dell'ASP.NET in AzureStep 5: Deploying Your ASP.NET Core App to Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="see-also"></a>Vedere anche

- [Introduzione a Swashbuckle e ad ASP.NET Core](/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio)
- [Pagine della Guida dell'API Web ASP.NET Core con Swagger/OpenAPI](/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-2.2)