---
title: Come usare un feed NuGet personalizzato con Connected Environment | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 03/27/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Usare un feed NuGet per accedere e usare pacchetti NuGet in un ambiente Connected Environment.
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: douge
ms.openlocfilehash: 71fcf1c3cfb37d783de13514f6a048c3b3711a53
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031221"
---
#  <a name="use-a-custom-nuget-feed-in-a-connected-environment"></a>Usare un feed NuGet personalizzato con Connected Environment

Un feed NuGet è un metodo pratico per includere origini dei pacchetti in un progetto. Per l'installazione corretta delle dipendenze nel contenitore Docker, Connected Environment deve avere accesso a questo feed.

Per impostare un feed NuGet:
1. Aggiungere un [riferimento al pacchetto](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files) nel file `*.csproj` sotto il nodo `PackageReference`.

   ```xml
   <ItemGroup>
       <!-- ... -->
       <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0" />
       <!-- ... -->
   </ItemGroup>
   ```

2. Creare un file [NuGet.Config](https://docs.microsoft.com/en-us/nuget/reference/nuget-config-file) nella cartella del progetto.
     * Usare la sezione `packageSources` per fare riferimento al percorso del feed NuGet. Importante: il feed NuGet deve essere accessibile pubblicamente.
     * Usare la sezione `packageSourceCredentials` per configurare le credenziali nome utente e password. 

   ```xml
   <packageSources>
       <add key="Contoso" value="https://contoso.com/packages/" />
   </packageSources>

   <packageSourceCredentials>
       <Contoso>
           <add key="Username" value="user@contoso.com" />
           <add key="ClearTextPassword" value="33f!!lloppa" />
       </Contoso>
   </packageSourceCredentials>
   ```

3. Se si usa il controllo del codice sorgente:
    - Aggiungere un riferimento a `NuGet.Config` nel file `.gitignore` per evitare di eseguire accidentalmente il commit di credenziali nel repository di origine.
    - Aprire il file `vsce.yaml` nel progetto, trovare la sezione `build` e inserire il frammento di codice seguente per assicurarsi che il file `NuGet.Config` verrà sincronizzato con Azure e usato durante il processo di compilazione dell'immagine del contenitore. Per impostazione predefinita, Connected Environment non sincronizza i file che corrispondono alle regole `.gitignore` e `.dockerignore`.

        ```yaml
        build:
        useGitIgnore: true
        ignore:
        - “!NuGet.Config”
        ```


## <a name="next-steps"></a>Passaggi successivi

Dopo aver completato i passaggi precedenti, quando si torna a eseguire `vsce up` (o si raggiunge `F5` in VSCode o Visual Studio), Connected Environment sincronizza il file `NuGet.Config` con Azure, quindi il file viene usato da `dotnet restore` per installare dipendenze del pacchetto nel contenitore.

