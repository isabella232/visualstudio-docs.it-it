---
title: Installare i certificati necessari per l'installazione offline di Visual Studio | Microsoft Docs
description: Informazione sulla procedura di installazione dei certificati per un'installazione offline di Visual Studio.
ms.date: 08/30/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70147dac62ad0aaa59a1c6823b321afe54b2d3a7
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2018
ms.locfileid: "43139124"
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Installare i certificati necessari per l'installazione offline di Visual Studio

Visual Studio è progettato per essere installato su un computer connesso a Internet, poiché molti componenti vengono aggiornati regolarmente. Con alcuni passaggi aggiuntivi, tuttavia, è possibile distribuire Visual Studio anche in un ambiente in cui non è disponibile una connessione Internet.

Il motore di installazione di Visual Studio installa solo contenuti attendibili. Per eseguire questa operazione, verificare le firme Authenticode dei contenuti scaricati e, prima di installarli, controllare l'attendibilità di tutti i contenuti. In questo modo l'ambiente rimane protetto dagli attacchi caratterizzati dalla compromissione del percorso di download. L'installazione di Visual Studio richiede pertanto l'installazione e l'aggiornamento nel computer dell'utente di diversi certificati Microsoft radice e intermedi standard. Se la macchina è stata mantenuta aggiornata con Windows Update, in genere i certificati di firma sono aggiornati. Se il computer è connesso a internet, durante l'installazione Visual Studio può aggiornare i certificati necessari per verificare le firme dei file. Se il computer è offline, i certificati devono essere aggiornati in un altro modo.

## <a name="how-to-refresh-certificates-when-offline"></a>Come aggiornare i certificati offline

Sono disponibili tre opzioni per l'installazione o aggiornamento dei certificati in un ambiente offline.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>Opzione 1: installare manualmente i certificati da una cartella di layout

Quando si crea un layout di rete, i certificati necessari vengono scaricati nella cartella Certificates. È quindi possibile installare manualmente i certificati facendo doppio clic su ogni file di certificato e seguendo la procedura guidata del gestore di certificati. Se viene richiesto di immettere una password, lasciare il campo vuoto.

**Aggiornamento**: per Visual Studio 2017 versione 15.8 Preview 2 o versioni successive, è possibile installare manualmente i certificati: fare clic su ognuno dei file di certificato con il pulsante destro del mouse, scegliere Installa certificato e quindi eseguire i vari passaggi della procedura guidata di Gestione certificati.

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>Opzione 2: distribuire certificati radice trusted in un ambiente aziendale

Per le aziende con computer offline che non hanno i certificati radice più recenti, un amministratore può usare le istruzioni riportate alla pagina [Configurazione di radici attendibili e di certificati non consentiti](https://technet.microsoft.com/library/dn265983.aspx) per eseguire l'aggiornamento.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Opzione 3: installare i certificati come parte di una distribuzione con script di Visual Studio

Se si sta eseguendo lo scripting di distribuzione di Visual Studio in un ambiente offline per le workstation client, è necessario seguire questa procedura:

1. Copiare lo [strumento gestore di certificati](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) nella condivisione di installazione, ad esempio \\server\condivisione\vs2017. Certmgr.exe non è incluso all'interno di Windows, ma è disponibile all'interno di [Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. Creare un file batch con i comandi seguenti:

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```
   **Aggiornamento**: per Visual Studio 2017 versione 15.8 Preview 2 o versioni successive, creare il file batch con i comandi seguenti:

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestSignCertificates.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignCertificates.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.SignCertificates.cer -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

3. Distribuire il file batch al client. Questo comando deve essere eseguito da un processo con privilegi elevati.

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Quali sono i file dei certificati nella cartella Certificates?

I tre file con estensione P12 in questa cartella contengono ognuno un certificato intermedio e un certificato radice. La maggior parte dei sistemi mantenuti aggiornati con Windows Update ha già installato questi certificati.

* **ManifestSignCertificates.p12** contiene:
    * Certificato intermedio: **Microsoft Code Signing PCA 2011**
        * Non richiesto Se presente, migliora le prestazioni in alcuni scenari.
    * Certificato radice: **Microsoft Root Certificate Authority 2011**
        * Obbligatorio per i sistemi Windows 7 Service Pack 1 in cui non sono installati gli ultimi aggiornamenti di Windows Updates.
* **ManifestCounterSignCertificates.p12** contiene:
    * Certificato intermedio: **Microsoft Time-Stamp PCA 2010**
        * Non richiesto Se presente, migliora le prestazioni in alcuni scenari.
    * Certificato radice: **Microsoft Root Certificate Authority 2010**
        * Obbligatorio per i sistemi Windows 7 Service Pack 1 in cui non sono installati gli ultimi aggiornamenti di Windows Updates.
* **Vs_installer_opc. SignCertificates.p12** contiene:
    * Certificato intermedio: **Microsoft Code Signing PCA**
        * Obbligatorio per tutti i sistemi. Si noti che i sistemi in tutti gli aggiornamenti sono stati applicati da Windows Update potrebbero non disporre di questo certificato.
    * Certificato radice: **Microsoft Root Certificate Authority**
        * Obbligatorio. Questo certificato viene fornito con i sistemi che eseguono Windows 7 o versione successiva.

**Aggiornamento**: per Visual Studio 2017 versione 15.8 Preview 2 o versioni successive, il programma di installazione di Visual Studio richiede l'installazione solo dei certificati radice nel sistema.

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Perché i certificati della cartella Certificates non vengono installati automaticamente?

Se una firma viene verificata in un ambiente online, per scaricare e aggiungere i certificati al sistema vengono usate le API di Windows. È nel corso di questo processo che, tramite impostazioni amministrative, si verifica se il certificato è attendibile e consentito. Questo processo di verifica, tuttavia, non può aver luogo nella maggior parte degli ambienti offline. Con l'installazione manuale dei certificati, gli amministratori all'interno delle aziende possono verificare che i certificati siano attendibili e soddisfino i criteri di sicurezza dell'organizzazione.

## <a name="checking-if-certificates-are-already-installed"></a>Verifica della presenza dei certificati

Un modo per eseguire questa verifica nel sistema di installazione corrisponde all'esecuzione di questa procedura:
1. Eseguire **mmc.exe**.<br/>
  a. Fare clic su File e scegliere **Aggiungi/Rimuovi snap-in**.<br/>
  b. Fare doppio clic su **Certificati**, selezionare l'**account computer** e fare clic su **Avanti**.<br/>
  c. Selezionare **Computer locale**, fare clic su **Fine** e fare clic su **OK**.<br/>
  d. Espandere **Certificati (computer locale)**.<br/>
  e. Espandere **Autorità di certificazione radice attendibili** e selezionare **Certificati**.<br/>
    * Controllare in questo elenco i certificati radice necessari.<br/>

   f. Espandere **Autorità di certificazione intermedie** e selezionare **Certificati**.<br/>
    * Controllare in questo elenco i certificati intermedi obbligatori.<br/>

2. Fare clic su File e scegliere **Aggiungi/Rimuovi snap-in**.<br/>
  a. Fare doppio clic su **Certificati**, selezionare **Account utente**, fare clic su **Fine** e quindi su **OK**.<br/>
  b. Espandere **Certificati - Utente corrente**.<br/>
  c. Espandere **Autorità di certificazione intermedie** e selezionare **Certificati**.<br/>
    * Controllare in questo elenco i certificati intermedi obbligatori.<br/>

Se i nomi dei certificati non sono presenti nelle colonne **Rilasciato a**, è necessario installare i certificati.  Se un certificato intermedio è presente solo nell'archivio dei certificati intermedi **Utente corrente**, è disponibile solo per l'utente connesso. Potrebbe essere necessario installarlo per altri utenti.

## <a name="install-visual-studio"></a>Installare Visual Studio

Dopo aver installato i certificati, la distribuzione di Visual Studio può procedere seguendo le istruzioni dalla sezione [Distribuzione da un'installazione di rete](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation) della pagina "Creare un'installazione di rete di Visual Studio".

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Visual Studio](install-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
