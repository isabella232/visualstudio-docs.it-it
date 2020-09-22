---
title: Personalizzare un codespace (anteprima)
description: Altre informazioni su come personalizzare uno spazio.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: f63dc4989a59256a0a3ad59491b2290912ffd2f8
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90862177"
---
# <a name="how-to-customize-a-codespace-preview"></a>Come personalizzare un codespace (anteprima)

Gli spazi dei codespace GitHub forniscono un ambiente di sviluppo completo nel cloud. Per lo sviluppo basato su Windows con Visual Studio 2019, le istanze predefinite di GitHub codespaces forniscono un ottimo punto di partenza, ma è anche possibile personalizzare l'ambiente per il progetto specifico.

## <a name="installed-software"></a>Software installato

Gli spazi dei codebase di Windows sono dotati di molti Framework e strumenti già installati, per poter iniziare subito. Nella tabella seguente sono elencate le applicazioni e le funzionalità disponibili in tutti gli ambienti codespace di Windows.

| App                                         | Alias percorso | Versione            |
|---------------------------------------------|------------|--------------------|
| .NET                                        | N/D        | 4.8                |
| Runtime di .NET Core                           | dotnet     | 2,1, 3,1           |
| .NET Core SDK                               | dotnet     | 2,1, 3.1.3, 3.1.4  |
| Interfaccia della riga di comando di Azure                                   | AZ         | 2.5                |
| Cioccolatoso                                  | Choco      | 0.10.15            |
| CMake                                       | CMake      | 3,17               |
| Git                                         | git        | 2.26               |
| Microsoft Build                             | msbuild    | 16.7               |
| Edizione di Microsoft SQL Server Express 2019   | N/D        | 15.0               |
| Ninja                                       | Ninja      | 1.8.2              |
| Node.js                                     | node       | 12.16              |
| NPM                                         | npm        | 6.14               |
| Python                                      | python     | 3,7                |
| Gestione pacchetti VC                          | vcpkg      | 2020,02            |
| Windows SDK                                 | N/D        | 10.0.18362         |

L'elenco precedente non è esaustivo ed esclude molti strumenti installati da Visual Studio, ad esempio IISExpress. Un componente può avere anche una versione secondaria o di patch diversa da quella indicata in precedenza.

Dettagli specifici sui Framework preinstallati e sugli strumenti sono disponibili nella sezione [specifiche software installate](#installed-software-specifics) di seguito.

## <a name="modifications-to-a-codespace"></a>Modifiche a un codespace
 
Una volta creato uno spazio di codespace, tutte le modifiche apportate a tale codespace specifico vengono rese permanente mentre l'istanza codespace è disponibile negli spazi dei codebase di GitHub. È possibile clonare repository aggiuntivi, installare strumenti e generatori di applicazioni e aggiungere altre risorse di sviluppo e tali modifiche verranno mantenute anche quando lo spazio di codespace viene sospeso. Tuttavia, se si elimina un codespace, le modifiche non vengono apportate.

> [!NOTE]
> Se si elimina un codespace, le eventuali modifiche apportate a un repository locale (in sospeso o sottoposto a commit) nell'area codespace andranno perse. Assicurarsi di effettuare il push delle modifiche al repository in una posizione remota prima di eliminare uno spazio.

Quando si è connessi a uno spazio dei nomi con Visual Studio, è possibile usare il terminale di Visual Studio per l'esecuzione degli strumenti da riga di comando. È possibile usare PowerShell o il prompt dei comandi di Windows, entrambi con privilegi elevati con l'account Administrator locale. Per altre informazioni sul terminale di Visual Studio, vedere il [Blog di annuncio sul terminale di Visual Studio](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/).

## <a name="customize-a-codespace"></a>Personalizzare un codespace

Il valore reale degli spazi dei nomi in GitHub si verifica quando è possibile creare ambienti di sviluppo unici e ripetibili nel cloud, personalizzati per il proprio lavoro e per il team. Compilando in un'istanza predefinita di GitHub codespaces, è possibile personalizzare ciò che viene installato e configurato quando si crea un nuovo codespace.

Nelle sezioni successive verranno descritti due metodi di configurazione dello spazio dei campi utilizzando *.devcontainer.js* e *.devinit.jssui* file. Questi file consentono di configurare i Framework di installazione e gli strumenti per uno spazio dei dati e, quando vengono aggiunti al repository, chiunque crei uno spazio dei dati basato sul repository avrà lo stesso ambiente di sviluppo remoto.

## <a name="customize-with-devcontainerjson"></a>Personalizzare con devcontainer.json

Quando viene creato uno spazio dei nomi, lo spazio dei nomi di GitHub Cerca un [*devcontainers.js*](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) nel file nella radice del repository e usa le impostazioni in per personalizzare lo spazio dei nomi o le istanze client che vi si connettono (browser-base Editor, Visual Studio o Visual Studio Code). La maggior parte delle impostazioni *devcontainer.jssulle* impostazioni si applicano agli spazi dei nomi basati su Linux o ad altri due client, ma alcuni sono disponibili per gli spazi dei nomi di Windows e Visual Studio.

Il *devcontainer.jssu* file può essere inserito in una delle due posizioni di un repository:

1. *{repository-root}/.devcontainer.js*
2. *{repository-root}/.devcontainer/devcontainer.json*

Gli spazi dei codice GitHub supportano le *devcontainer.jsseguenti nelle* proprietà. L'impostazione di Visual Studio Code proprietà specifiche è utile se si prevede di connettersi al codespace con gli altri client oltre a Visual Studio. 

* `extensions` : Una matrice di [Visual Studio Code](https://marketplace.visualstudio.com/vscode) estensioni del Marketplace da installare.
* `settings`  : Set di [impostazioni Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings) da applicare.
* `forwardPorts`-Una porta o una matrice di porte che devono essere automaticamente trasmesse localmente quando viene eseguito lo spazio dei nomi.
* `postCreateCommand` : Stringa di comando o elenco di argomenti di comando da eseguire dopo la creazione dello spazio dei nomi.

> [!NOTE]
> **devcontainer.jssui** file vengono usati anche per supportare Visual Studio Code [lo sviluppo remoto](https://code.visualstudio.com/docs/remote/remote-overview)e avere proprietà aggiuntive non analizzate in questo documento. Queste proprietà aggiuntive sono sicure da aggiungere al file, ma verranno ignorate da codespaces. Per ulteriori informazioni, vedere il [devcontainer.jsdi riferimento](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) su code.VisualStudio.com.

## <a name="customize-with-devinit"></a>Personalizza con devinilt

[devinit](../../devinit/getting-started-with-devinit.md) è uno strumento da riga di comando incluso negli spazi dei nomi di Windows che consente di installare Framework e strumenti nell'ambiente in uso. È possibile eseguirlo manualmente da un prompt dei comandi ( `devinit -t require-dotnetcoresdk` ), ma la sua vera potenza deriva dalla creazione di un [ *.devinit.jspersonalizzato in* ](../../devinit/devinit-json.md) un file per configurare in modo uniforme uno spazio dei comandi quando ne viene creato uno.

`devinit` include un set di strumenti per l'installazione di elementi specifici, ad esempio SQL Server e l'interfaccia della riga di comando di Azure, nonché per l'esecuzione di gestori di pacchetti generali come Chocolate, NPM e vcpkg. Per l'elenco completo degli `devinit` strumenti, vedere la documentazione relativa agli [strumenti disponibili](../../devinit/devinit-tool-list.md) .

### <a name="devinitjson"></a>devinit.js

Sebbene sia possibile eseguire `devinit` direttamente la riga di comando, è consigliabile creare [*devinit.jsnei*](../../devinit/devinit-json.md) file di configurazione, che descrivono il set di `devinit` strumenti da eseguire. 

Ad esempio, per installare il [.NET Core SDK](https://docs.microsoft.com/dotnet/core/sdk), un *.devinit.jsin* avrà un aspetto simile al seguente:

```json
{
    "run": [
        {
            "comments": "We need the .NET Core SDK."
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

Quando si crea un *.devinit.js* nel file nella radice del progetto, verrà usato quando si esegue `devinit init` . Per impostazione predefinita, `devinit.exe` Cerca il file nei percorsi seguenti:

1. *{Current-directory} \\.devinit.js*
2. *{Current-directory} \\.devinit\devinit.js*

### <a name="running-devinit-when-creating-a-codespace"></a>Esecuzione di devinit durante la creazione di un codespace

È possibile impostare gli spazi dei codebase di GitHub in modo che vengano eseguiti `devinit` dopo la creazione di un codespace usando la `postCreateCommand` Proprietà in un *devcontainers.jssu* file. Come indicato in precedenza, gli spazi dei codebase di GitHub cercheranno un *devcontainer.jssul* file nel repository clonato per personalizzare l'istanza codespace o client e verrà eseguito qualsiasi comando descritto nella `postCreateCommand` Proprietà.

Specificando `devinit init` , `devinit` verrà eseguito utilizzando il *devinit.jsnella* configurazione.

```json
{
  "postCreateCommand": "devinit init"
}
```

### <a name="an-example"></a>Esempio

Ecco un semplice esempio di installazione di .NET Core Entity Framework strumento da riga di comando, `dotnet-ef` .

**devcontainer.js**

Contenuto del *.devcontainer.js* nel file nella radice del repository. 

```json
{
  "postCreateCommand": "devinit init"
}
```

**devinit.js**

Contenuto del *.devinit.jssu* file. Questo file deve trovarsi nella stessa cartella del *.devcontainer.js*.

```json
{
    "run": [
        {
            "comments": "Install the Entity Framework tools",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
        }
     ]
}
```

È possibile trovare altri `devinit` esempi nell' `devinit` [elenco degli esempi](../../devinit/sample-readme.md).

## <a name="port-forwarding"></a>Port forwarding

Gli spazi dei codebase di GitHub forniscono l'accesso alle applicazioni e ai servizi in esecuzione negli ambienti remoti per mezzo dell'invio del Port. Per impostazione predefinita, nessuna porta viene trasmessa per motivi di sicurezza. È tuttavia possibile specificare determinate porte da aprire in un codespace.

### <a name="configure-port-forwarding"></a>Configurare il port forwarding

Se per un repository specifico sono presenti una o più porte da trasmettere per impostazione predefinita, è possibile configurarle in *devcontainer.js* con la `forwardPorts` Proprietà.

* `forwardPorts` : Una porta o una matrice di porte che devono essere automaticamente trasmesse localmente quando l'ambiente è in esecuzione.

## <a name="installed-software-specifics"></a>Specifiche software installate

### <a name="microsoft-sql-server"></a>Microsoft SQL Server

Microsoft SQL Server 2019 Express Edition è disponibile e in esecuzione come servizio locale nell'ambiente codespace di Windows. L'utente corrente, a cui viene eseguita l'app e il terminale di Visual Studio, dispone dei diritti di amministratore SQL per SQL Server. Per amministrare il server, è necessario usare PowerShell nel terminale di Visual Studio o in altri strumenti da riga di comando, ad esempio `dotnet-ef` . Attualmente SQL Server Management Studio e altri strumenti di amministrazione remota non sono disponibili.

#### <a name="example-connection-string"></a>Stringa di connessione di esempio

Di seguito è riportato un esempio di una stringa di connessione per la connessione al server MS SQL locale.

```csharp
"Server=(LocalDB);Integrated Security=true;"
```

### <a name="azure-cli"></a>Interfaccia della riga di comando di Azure

L'interfaccia della riga di comando di Azure è installata in tutti gli ambienti codespace di Windows ed è disponibile nel percorso come `az` .

#### <a name="using-azure-resources"></a>Uso delle risorse di Azure

Se si usa un'identità Azure Active Directory per autenticare l'applicazione in base alle risorse di Azure, sarà necessario prima accedere ad Azure dal terminale di Visual Studio. Per accedere, usare il comando dell'interfaccia della riga di comando di Azure `login` con il flusso di accesso del dispositivo (come illustrato nell'esempio seguente). Una volta effettuato l'accesso, l'applicazione e la sessione terminal dovrebbero essere in grado di usare tale identità.

```powershell
> az login --use-device-code
```

Per altre informazioni sul `az login` comando, vedere la [documentazione](/cli/azure/reference-index#az_login)dell'interfaccia della riga di comando di Azure.

## <a name="see-also"></a>Vedere anche

- [Che cosa sono gli spazi di dati di GitHub?](codespaces-overview.md)
- [Come usare Visual Studio con un codespace](use-visual-studio-with-codespaces.md)