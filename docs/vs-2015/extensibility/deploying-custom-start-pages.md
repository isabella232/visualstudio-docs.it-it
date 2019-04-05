---
title: Distribuzione di pagine iniziali personalizzate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dcf653654005b75a889bcafd668fbb9313572ff2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001361"
---
# <a name="deploying-custom-start-pages"></a>Distribuzione di pagine iniziali personalizzate
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile distribuire le pagine iniziali personalizzate tramite distribuzione VSIX oppure copiando i file nelle posizioni corrette nel computer di destinazione.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Distribuzione VSIX usando il modello di progetto di pagina iniziale  
 Quando si crea una pagina iniziale usando il modello di progetto di pagina iniziale e quindi compilare il progetto, Visual Studio crea un file con estensione VSIX che è possibile distribuire. Creazione del pacchetto di una pagina iniziale in un file con estensione VSIX ti offre le opzioni seguenti per la distribuzione, a seconda dei destinatari desiderati:  
  
- È possibile inserire il file VSIX in una condivisione di rete o in un sito Web pubblico. Quando un utente apre il file, viene installata automaticamente nella pagina iniziale.  
  
- È possibile caricare il file VSIX per la [Visual Studio Marketplace](https://marketplace.visualstudio.com/) del sito Web in modo che gli utenti possono installarla tramite **gestore estensioni del**.  
  
  Il modello di progetto di pagina iniziale Crea una copia del valore predefinito la pagina iniziale di Visual Studio in modo che è possibile modificare la copia e conservare l'originale.  
  
  È possibile ottenere il modello di progetto di pagina iniziale usando **gestore estensioni del** o scaricandolo dal sito Web.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Distribuzione VSIX senza usare il modello di progetto di pagina di avvio  
 Una corretta distribuzione VSIX richiede un'estensione per essere installati nelle cartelle che sono riconosciute dal processo di registrazione VSIX e da **gestore estensioni del**. Poiché il modello di progetto di pagina iniziale specifica già nelle cartelle corrette, è consigliabile usarla ogni volta che si desidera creare un pacchetto di un'estensione per la distribuzione di VSIX. Tuttavia, se si dispone di un caso in cui non è possibile utilizzare il modello, è possibile creare una distribuzione VSIX senza usarlo.  
  
 Per creare una distribuzione VSIX senza usare il modello di progetto di pagina iniziale, è prima di tutto creare un file con estensione VSIX per la pagina di avvio in uno dei due modi:  
  
- Aggiungendo i file della pagina iniziale personalizzati per un progetto VSIX vuoto. Per altre informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).  
  
- Quando si crea manualmente un file con estensione VSIX. Per altre informazioni, vedere [Procedura: Creare manualmente il pacchetto estensione (distribuzione VSIX)](../misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
  Per Visual Studio riconosca una pagina iniziale, il `Content Element` del manifesto VSIX deve contenere un `CustomExtension Element` con il `Type` attributo impostato su `"StartPage"`. Viene visualizzata un'estensione di pagina iniziale che è stata installata utilizzando la distribuzione VSIX nel **Personalizza pagina iniziale** elenco il **avvio** pagina Opzioni come **[estensione installata]** *Nome dell'estensione*.  
  
  Se il pacchetto di pagina iniziale include gli assembly, è necessario aggiungere la registrazione di percorso di associazione in modo che siano disponibili quando si avvia Visual Studio. A tale scopo, assicurarsi che il pacchetto includa un file. pkgdef che contiene le informazioni seguenti.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>Distribuzione VSIX per tutti gli utenti  
 Per impostazione predefinita, le estensioni distribuite nei pacchetti VSIX installare solo per l'utente corrente. È possibile apportare un'installazione di pagina iniziale per tutti gli utenti del computer di destinazione mediante la creazione di una distribuzione di tutti gli utenti.  
  
##### <a name="to-create-an-all-users-deployment"></a>Per creare una distribuzione di tutti gli utenti  
  
1.  Aprire il file extension vsixmanifest in visualizzazione codice.  
  
2.  Nel `Identifier` elemento del manifesto vsix, aggiungere un' `AllUsers` elemento che ha il valore `true`.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     In questo modo il programma di installazione vsix richiede le autorizzazioni di amministratore e quindi installare i file a \Common7\IDE\Extensions.  
  
3.  Aprire il file pkgdef.  
  
4.  Modificare il pkgdef per impostare la pagina iniziale predefinita in HKLM aggiungendo il codice seguente, dove *MyStartPage.xaml* è il nome del file con estensione XAML contenente la pagina iniziale.  
  
     [$RootKey$\StartPage\Default]  
  
     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"  
  
     In questo modo si Visual per la ricerca nella nuova posizione della pagina iniziale.  
  
## <a name="file-copy-deployment"></a>Distribuzione tramite Copia file  
 Non è necessario creare un file con estensione VSIX per la distribuzione di una pagina iniziale personalizzata. In alternativa, è possibile copiare il markup e i file di supporto direttamente nella cartella \StartPages\ dell'utente. Il **Personalizza pagina iniziale** elenco il **avvio** pagina Opzioni Elenca tutti i file con estensione XAML in tale cartella, con il percorso, ad esempio, %USERPROFILE%\My Documents\Visual Studio  *versione*\StartPages\\*nome File*. Xaml. Se la pagina iniziale include i riferimenti agli assembly privato, è necessario copiarli e incollarli nella cartella \privateassemblies\..  
  
 Per distribuire una pagina iniziale creato senza creazione dei pacchetti in un file con estensione VSIX, è consigliabile che si usa una strategia di copia di file di base, ad esempio, uno script batch o qualsiasi altra tecnologia di distribuzione che consente di inserire i file nelle directory necessaria.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>Per installare manualmente una pagina iniziale personalizzata  
  
1.  Copiare il file con estensione XAML contenente il markup della pagina iniziale, insieme a eventuali file di supporto diverso da assembly e incollarli nella cartella \StartPages\ dell'utente.  
  
2.  Se la pagina iniziale richiede l'assembly, copiarli e incollarli in... \\ *Cartella di installazione di visual Studio*\Common7\IDE\PrivateAssemblies.\\.  
  
3.  Nel **Personalizza pagina iniziale** elenco le **avvio** le opzioni di pagina, selezionare la nuova pagina iniziale. Per altre informazioni, vedere [Personalizzazione della pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione della pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Aggiunta di un controllo utente nella pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)
