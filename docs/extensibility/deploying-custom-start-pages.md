---
title: Distribuzione di pagine iniziali personalizzate | Microsoft Docs
description: Informazioni su come distribuire pagine iniziali personalizzate usando la distribuzione VSIX o copiando i file nei percorsi corretti nel computer di destinazione.
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
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: a356fe3dadaf0eca4f0b4d0f2a7d17f0b475acfb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061407"
---
# <a name="deploy-custom-start-pages"></a>Distribuire pagine iniziali personalizzate

È possibile distribuire pagine iniziali personalizzate usando la distribuzione VSIX o copiando i file nei percorsi corretti nel computer di destinazione.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Distribuzione VSIX tramite il modello di progetto di pagina iniziale

Quando si crea una pagina iniziale usando il modello di progetto di pagina iniziale e quindi si compila il progetto, Visual Studio crea un file con *estensione VSIX* che è possibile distribuire. Il packaging di una pagina iniziale in un file con *estensione VSIX* offre le opzioni seguenti per la distribuzione, a seconda dei destinatari desiderati:

- È possibile inserire il file con *estensione VSIX* in una condivisione di rete o in un sito Web pubblico. Quando un utente apre il file, la pagina iniziale viene installata automaticamente.

- È possibile caricare il file *VSIX* nel sito Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) in modo che gli utenti possano installarlo utilizzando **Gestione estensioni**.

Il modello di progetto di pagina iniziale crea una copia della pagina iniziale predefinita di Visual Studio in modo che sia possibile modificare la copia e conservare l'originale.

È possibile ottenere il modello di progetto di pagina iniziale usando **Gestione estensioni** oppure eseguendone il download dal sito Web.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Distribuzione VSIX senza usare il modello di progetto di pagina iniziale
 Una distribuzione VSIX riuscita richiede l'installazione di un'estensione in cartelle riconosciute dal processo di registrazione VSIX e da **Gestione estensioni**. Poiché il modello di progetto di pagina iniziale specifica già le cartelle corrette, è consigliabile utilizzarlo ogni volta che si desidera creare un pacchetto di un'estensione per la distribuzione VSIX. Tuttavia, se si ha un caso in cui non è possibile usare il modello, è possibile creare una distribuzione VSIX senza usarla.

 Per creare una distribuzione VSIX senza usare il modello di progetto di pagina iniziale, creare prima di tutto un file *VSIX* per la pagina iniziale in uno dei due modi seguenti:

- Aggiungendo i file della pagina iniziale personalizzati a un progetto VSIX vuoto. Per altre informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).

- Creando manualmente un file con *estensione VSIX* . Per creare un file con *estensione VSIX* manualmente:

   1. Creare il file con *estensione vsixmanifest* e il file *[Content_Types]. XML* in una nuova cartella. Per altre informazioni, vedere [anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md).

   2. In Esplora risorse fare clic con il pulsante destro del mouse sulla cartella che contiene i due file XML, scegliere **Invia a** e quindi fare clic su cartella compressa. Rinominare il file *zip* risultante in *nomefile. vsix*, dove nomefile è il nome del file ridistribuibile che installa il pacchetto.

Affinché Visual Studio riconosca una pagina iniziale, il `Content Element` del manifesto VSIX deve contenere un oggetto `CustomExtension Element` il cui `Type` attributo è impostato su `"StartPage"` . Un'estensione della pagina iniziale che è stata installata tramite la distribuzione VSIX viene visualizzata nell'elenco **Personalizza pagina iniziale** della pagina Opzioni di **avvio** come *Nome estensione* **[estensione installata]** .

Se il pacchetto della pagina iniziale include gli assembly, è necessario aggiungere la registrazione del percorso di associazione in modo che siano disponibili all'avvio di Visual Studio. A tale scopo, verificare che il pacchetto includa un file con *estensione pkgdef* con le informazioni seguenti.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Distribuzione VSIX per tutti gli utenti
 Per impostazione predefinita, le estensioni distribuite nei pacchetti VSIX vengono installate solo per l'utente corrente. È possibile eseguire un'installazione della pagina iniziale per tutti gli utenti del computer di destinazione creando una distribuzione All-Users.

### <a name="to-create-an-all-users-deployment"></a>Per creare una distribuzione All-Users

1. Aprire il file *Extension. vsixmanifest* nella visualizzazione codice.

2. Nell' `Identifier` elemento del manifesto VSIX aggiungere un `AllUsers` elemento con il valore `true` .

    ```
    <AllUsers>true</AllUsers>
    ```

     In questo modo il programma di installazione VSIX richiederà le autorizzazioni di amministratore e quindi installerà i file in *\Common7\IDE\Extensions*.

3. Aprire il file con *estensione pkgdef* .

4. Modificare il file con *estensione pkgdef* per impostare la pagina iniziale predefinita in HKLM aggiungendo quanto segue, dove *StartPage. XAML* è il nome del file con *estensione XAML* che contiene la pagina iniziale.

     [$RootKey $ \StartPage\Default]

     "URI" = "$PackageFolder $ \\ *StartPage. XAML*"

     Ciò indica a Visual Studio di esaminare la nuova posizione della pagina iniziale.

## <a name="file-copy-deployment"></a>Distribuzione copia file
 Non è necessario creare un file con *estensione VSIX* per distribuire una pagina iniziale personalizzata. In alternativa, è possibile copiare i file di markup e di supporto direttamente nella <em>cartella \StartPages dell'utente \* . L'elenco **Personalizza pagina iniziale</em>* nella pagina Opzioni di **avvio** elenca tutti i file con *estensione XAML* in tale cartella, insieme al percorso, ad esempio *%USERPROFILE%\My Documenti\Visual Studio {Version} \StartPages \\ {nome file}. XAML*. Se la pagina iniziale include riferimenti a assembly privati, è necessario copiarli e incollarli nella cartella * \PrivateAssemblies \* .

 Per distribuire una pagina iniziale creata senza crearne il pacchetto in un file con *estensione VSIX* , è consigliabile usare una strategia di copia di base dei file, ad esempio uno script batch o qualsiasi altra tecnologia di distribuzione che consenta di inserire i file nelle directory richieste.

### <a name="to-manually-install-a-custom-start-page"></a>Per installare manualmente una pagina iniziale personalizzata

1. Copiare il file con *estensione XAML* che contiene il markup della pagina iniziale, insieme a tutti i file di supporto diversi dagli assembly, e incollarli nella cartella * \StartPages dell'utente \* .

2. Se la pagina iniziale richiede assembly, copiarli e incollarli in *. \\ {Cartella di installazione di Visual Studio \\ } \Common7\IDE\PrivateAssemblies*.

3. Nell'elenco **Personalizza pagina iniziale** della pagina Opzioni di **avvio** selezionare la nuova pagina iniziale. Per ulteriori informazioni, vedere [personalizzare la pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Vedi anche

- [Personalizzare la pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md)
- [Aggiungere il controllo utente alla pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)
