---
title: Distribuzione di pagine iniziale personalizzate | Microsoft Docs
description: Informazioni su come distribuire pagine iniziale personalizzate usando la distribuzione VSIX o copiando i file nei percorsi corretti nel computer di destinazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 6cbe93af3737526a5adf1719f0f4b129cb3076a7dadaa2bade9a413e0a69407e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414922"
---
# <a name="deploy-custom-start-pages"></a>Distribuire pagine iniziale personalizzate

È possibile distribuire pagine iniziale personalizzate usando la distribuzione VSIX o copiando i file nei percorsi corretti nel computer di destinazione.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Distribuzione VSIX tramite il modello di progetto Pagina iniziale

Quando si crea una pagina iniziale usando il modello di progetto Pagina iniziale e quindi si compila il progetto, Visual Studio crea un file *vsix* che è possibile distribuire. La creazione di una pagina iniziale in un file con estensione *vsix* offre le opzioni seguenti per la distribuzione, a seconda dei destinatari:

- È possibile inserire il file *vsix* in una condivisione di rete o in un sito Web pubblico. Quando un utente apre il file, la pagina iniziale viene installata automaticamente.

- È possibile caricare il file *vsix* nel sito Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) in modo che gli utenti possano installarlo usando **Gestione estensioni**.

Il modello di progetto Pagina iniziale crea una copia della pagina iniziale Visual Studio predefinita in modo che sia possibile modificare la copia e mantenere l'originale.

È possibile ottenere il modello di progetto Pagina iniziale usando **Gestione estensioni** o scaricarlo dal sito Web.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Distribuzione VSIX senza usare il modello di progetto Pagina iniziale
 Una corretta distribuzione di VSIX richiede l'installazione di un'estensione nelle cartelle riconosciute dal processo di registrazione VSIX e da **Gestione estensioni**. Poiché il modello di progetto Pagina iniziale specifica già le cartelle corrette, è consigliabile usarlo ogni volta che si vuole creare un pacchetto di un'estensione per la distribuzione VSIX. Tuttavia, se si ha un caso in cui non è possibile usare il modello, è possibile creare una distribuzione VSIX senza usarlo.

 Per creare una distribuzione VSIX senza usare il modello di progetto Pagina iniziale, creare prima di tutto un file *vsix* per la pagina iniziale in uno dei due modi seguenti:

- Aggiungendo i file della pagina iniziale personalizzati a un Project VSIX vuoto. Per altre informazioni, vedere [Modello di progetto VSIX.](../extensibility/vsix-project-template.md)

- Creando manualmente un file *con estensione vsix.* Per creare manualmente un file *vsix:*

   1. Creare il file *extension.vsixmanifest* e il file *[Content_Types].xml* in una nuova cartella. Per altre informazioni, vedere [Anatomia di un pacchetto VSIX.](../extensibility/anatomy-of-a-vsix-package.md)

   2. In Windows Explorer fare clic con il pulsante destro del mouse sulla cartella contenente i due file XML, scegliere Invia a **e** quindi fare clic su Cartella compressa. Rinominare il file *.zip* in *Filename.vsix*, dove Nomefile è il nome del file ridistribuibile che installa il pacchetto.

Per Visual Studio riconoscere una pagina iniziale, l'elemento del manifesto VSIX deve contenere un elemento con `Content Element` `CustomExtension Element` l'attributo impostato su `Type` `"StartPage"` . Un'estensione della pagina iniziale installata tramite la  distribuzione VSIX viene  visualizzata nell'elenco Personalizza pagina iniziale della pagina Opzioni di avvio come **[Estensione installata]** *Nome estensione*.

Se il pacchetto della pagina iniziale include assembly, è necessario aggiungere la registrazione del percorso di associazione in modo che siano disponibili Visual Studio avvio. A tale scopo, assicurarsi che il pacchetto includa un file *con estensione pkgdef* con le informazioni seguenti.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Distribuzione VSIX per tutti gli utenti
 Per impostazione predefinita, le estensioni distribuite nei pacchetti VSIX vengono installate solo per l'utente corrente. È possibile eseguire un'installazione della pagina iniziale per tutti gli utenti del computer di destinazione creando una All-Users distribuzione.

### <a name="to-create-an-all-users-deployment"></a>Per creare una distribuzione All-Users distribuzione

1. Aprire il file *extension.vsixmanifest* nella visualizzazione codice.

2. `Identifier`Nell'elemento del manifesto vsix aggiungere un `AllUsers` elemento con valore `true` .

    ```
    <AllUsers>true</AllUsers>
    ```

     In questo modo il programma di installazione vsix richiede le autorizzazioni di amministratore e quindi installa i file in *\Common7\IDE\Extensions*.

3. Aprire il file *con estensione pkgdef.*

4. Modificare il file con estensione *pkgdef* per impostare la pagina iniziale predefinita in HKLM aggiungendo quanto segue, dove *MyStartPage.xaml* è il nome del file con estensione *xaml* che contiene la pagina iniziale.

     [$RootKey$\StartPage\Default]

     "Uri"="$PackageFolder$ \\ *MyStartPage.xaml*"

     Ciò indica Visual Studio ricerca nella nuova posizione della pagina iniziale.

## <a name="file-copy-deployment"></a>Distribuzione della copia file
 Non è necessario creare un file *vsix* per distribuire una pagina iniziale personalizzata. È invece possibile copiare il markup e i file di supporto direttamente nella cartella <em>\StartPages \* dell'utente. *</em>* L'elenco * Personalizza  pagina iniziale nella pagina Opzioni di avvio elenca tutti i file *con* estensione xaml in tale cartella, insieme al percorso, ad esempio *%USERPROFILE%\Documenti\Visual Studio {version}\StartPages \\ {Nome file}.xaml.* Se la pagina iniziale include riferimenti ad assembly privati, è necessario copiarli e incollarli nella cartella \* *\PrivateAssemblies.

 Per distribuire una pagina iniziale creata senza crearne il pacchetto in un file *vsix,* è consigliabile usare una strategia di copia di file di base, ad esempio uno script batch o qualsiasi altra tecnologia di distribuzione che consenta di inserire i file nelle directory necessarie.

### <a name="to-manually-install-a-custom-start-page"></a>Per installare manualmente una pagina iniziale personalizzata

1. Copiare il file con estensione *xaml* che contiene il markup della pagina iniziale, insieme a tutti i file di supporto diversi dagli assembly, e incollarli nella cartella *\StartPages \* dell'utente.

2. Se la pagina iniziale richiede assembly, copiarli e incollarli in *. \\ {Visual Studio cartella di installazione}\Common7\IDE\PrivateAssemblies \\*.

3. **Nell'elenco Personalizza pagina iniziale** della pagina **Opzioni** di avvio selezionare la nuova pagina iniziale. Per altre informazioni, vedere [Personalizzare la pagina iniziale.](../ide/customizing-the-start-page-for-visual-studio.md)

## <a name="see-also"></a>Vedi anche

- [Personalizzare la pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md)
- [Aggiungere il controllo utente alla pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)
