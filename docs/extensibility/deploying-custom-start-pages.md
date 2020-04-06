---
title: Distribuzione di pagine iniziali personalizzate Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 210b4589c0e2165af537c3fa9129affb06197e9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712235"
---
# <a name="deploy-custom-start-pages"></a>Distribuire pagine iniziali personalizzateDeploy custom Start Pages

È possibile distribuire pagine iniziali personalizzate utilizzando la distribuzione VSIX o copiando i file nei percorsi corretti nel computer di destinazione.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Distribuzione VSIX tramite il modello di progetto di pagina iniziale

Quando si crea una pagina iniziale utilizzando il modello di progetto di pagina iniziale e quindi compilare il progetto, Visual Studio crea un file *VSIX* che è possibile distribuire. La creazione del pacchetto di una pagina iniziale in un file VSIX offre le opzioni seguenti per la distribuzione, a seconda del gruppo di destinatari previsto:Packaging a Start Page in a *.vsix* file gives you the following options for deployment, depending on your intended audience:

- È possibile inserire il file *VSIX* in una condivisione di rete o in un sito Web pubblico. Quando qualcuno apre il file, la pagina iniziale viene installata automaticamente.

- È possibile caricare il file *VSIX* nel sito Web di [Visual Studio Marketplace](https://marketplace.visualstudio.com/) in modo che gli utenti possano installarlo utilizzando Gestione **estensioni.**

Il modello di progetto di pagina iniziale crea una copia della pagina iniziale predefinita di Visual Studio in modo che è possibile modificare la copia e mantenere l'originale.

È possibile ottenere il modello di progetto di pagina iniziale utilizzando **Gestione estensioni** o scaricandolo dal sito Web.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Distribuzione VSIX senza utilizzare il modello di progetto di pagina iniziale
 Una corretta distribuzione VSIX richiede l'installazione di un'estensione nelle cartelle riconosciute dal processo di registrazione VSIX e da **Extension Manager**. Poiché il modello di progetto di pagina iniziale specifica già le cartelle corrette, è consigliabile utilizzarlo ogni volta che si desidera creare un pacchetto di un'estensione per la distribuzione VSIX. Tuttavia, se si dispone di un caso in cui non è possibile utilizzare il modello, è possibile creare una distribuzione VSIX senza utilizzarlo.

 Per creare una distribuzione VSIX senza usare il modello di progetto di pagina iniziale, creare innanzitutto un file VSIX per la pagina iniziale in uno di questi due modi:To create a VSIX deployment without using the Start Page project template, first create a .vsix file for the Start Page in uno dei due modi seguenti:To create a VSIX deployment without using the Start Page project template, first create a *.vsix* file for the Start Page in uno dei due modi

- Aggiungendo i file della pagina iniziale personalizzata a un progetto VSIX vuoto. Per ulteriori informazioni, vedere modello di [progetto VSIX](../extensibility/vsix-project-template.md).

- Creando manualmente un file *VSIX.* Per creare manualmente un file *VSIX:*

   1. Creare il file *extension.vsixmanifest* e il file *[Content_Types].xml* in una nuova cartella. Per ulteriori informazioni, vedere [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md).

   2. In Esplora risorse fare clic con il pulsante destro del mouse sulla cartella contenente i due file XML, **scegliere Invia a**, quindi Cartella compressa. Rinominare il file *.zip* risultante in *Nomefile.vsix*, dove Nomefile è il nome del file ridistribuibile che installa il pacchetto.

Affinché Visual Studio riconosca `Content Element` una pagina iniziale, `CustomExtension Element` l'oggetto `Type` del `"StartPage"`manifesto VSIX deve contenere un oggetto con l'attributo impostato su . Un'estensione della pagina iniziale che è stata installata utilizzando la distribuzione VSIX viene visualizzata nell'elenco **Personalizza pagina iniziale** nella pagina Opzioni **di avvio** come **[Estensione installata]** *Nome estensione*.

Se il pacchetto della pagina iniziale include assembly, è necessario aggiungere la registrazione del percorso di associazione in modo che siano disponibili all'avvio di Visual Studio.If your Start Page package includes assemblies, you must add binding path registration so that they are available when Visual Studio starts. A tale scopo, assicurarsi che il pacchetto includa un file *con estensione pkgdef* contenente le informazioni seguenti.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Distribuzione VSIX per tutti gli utenti
 Per impostazione predefinita, le estensioni distribuite nei pacchetti VSIX vengono installate solo per l'utente corrente. È possibile eseguire un'installazione della pagina iniziale per tutti gli utenti del computer di destinazione creando una distribuzione per tutti gli utenti.

### <a name="to-create-an-all-users-deployment"></a>Per creare una distribuzione per tutti gli utenti

1. Aprire il file *extension.vsixmanifest* nella visualizzazione codice.

2. Nell'elemento `Identifier` del manifesto vsix `AllUsers` aggiungere un elemento `true`con valore di .

    ```
    <AllUsers>true</AllUsers>
    ```

     In questo modo il programma di installazione vsix richiedere le autorizzazioni di amministratore e quindi installare i file in *.*

3. Aprire il file *con estensione pkgdef.*

4. Modificare *il file con estensione pkgdef* per impostare la pagina iniziale predefinita in HKLM aggiungendo quanto segue, dove *MyStartPage.xaml* è il nome del file *xaml* che contiene la pagina iniziale.

     [$RootKey ,>PaginaInizio/Pagina iniziale/Predefinito]

     "Uri" $PackageFolder\\ *" MyStartPage.xaml*"

     Ciò indica a Visual Studio di cercare nel nuovo percorso della pagina iniziale.

## <a name="file-copy-deployment"></a>Distribuzione della copia dei file
 Non è necessario creare un file *VSIX* per distribuire una pagina iniziale personalizzata. Al contrario, è possibile copiare il markup e i file di supporto direttamente nella cartella dell'utente di <em>StartPages.\* L'elenco Personalizza*pagina</em> * iniziale nella pagina delle opzioni di **avvio** elenca tutti i file *con estensione xaml* in tale cartella, insieme al percorso, ad esempio *%USERPROFILE%\\*. Se la pagina iniziale include riferimenti ad assembly privati, è necessario\* copiarli e incollarli nella cartella PrivateAssemblies .

 Per distribuire una pagina iniziale creata senza creare il pacchetto in un file *VSIX,* è consigliabile utilizzare una strategia di copia dei file di base, ad esempio uno script batch o qualsiasi altra tecnologia di distribuzione che consenta di inserire i file nelle directory richieste.

### <a name="to-manually-install-a-custom-start-page"></a>Per installare manualmente una pagina iniziale personalizzata

1. Copiare il file *con estensione xaml* che contiene il markup della pagina iniziale, insieme a\* qualsiasi file di supporto diverso dagli assembly, e incollarli nella cartella dell'utente .

2. Se la pagina iniziale richiede assembly, copiarli e incollarli in *.. \\.\\*

3. Nell'elenco **Personalizza pagina iniziale** della pagina **Opzioni di avvio** selezionare la nuova pagina iniziale. Per ulteriori informazioni, consultate [Personalizzare la pagina iniziale.](../ide/customizing-the-start-page-for-visual-studio.md)

## <a name="see-also"></a>Vedere anche

- [Personalizzare la pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md)
- [Aggiungere il controllo utente alla pagina inizialeAdd user control to the Start Page](../extensibility/adding-user-control-to-the-start-page.md)
