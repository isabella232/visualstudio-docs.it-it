---
title: Installare e usare Visual Studio per Mac con un firewall o un server proxy
titleSuffix: ''
description: Questo documento fornisce un elenco di host da abilitare nel firewall per il corretto funzionamento di Visual Studio per Mac (e dei relativi carichi di lavoro, incluso Xamarin) in un ambiente aziendale.
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.openlocfilehash: 25a4597c8d523b63e7ceb0cf8b5eff71af58071a
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964460"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Installare e usare Visual Studio per Mac protetto da un firewall o un server proxy

Se un utente o un'organizzazione usa misure di sicurezza, come un firewall o un server proxy, è possibile che vi siano domini da aggiungere a un elenco di indirizzi consentiti, così come porte e protocolli da aprire per ottenere un'esperienza ottimale durante l'installazione e l'uso di Visual Studio per Mac e dei servizi di Azure.

- [**Install Visual Studio per Mac**](#install-visual-studio-for-mac): queste tabelle includono i domini che devono consentire la connettività in modo da poter accedere a tutte le funzionalità e i carichi di lavoro Visual Studio per Mac.

- [**Usare Visual Studio per Mac**](#use-visual-studio-for-mac): queste tabelle includono i domini che devono consentire la connettività in modo da poter accedere alle funzionalità correlate.

## <a name="install-visual-studio-for-mac"></a>Installare Visual Studio per Mac

Poiché il programma di installazione di Visual Studio per Mac esegue il download da diversi domini e server di download, ecco i domini e gli URL da aggiungere come attendibili nelle configurazioni.

### <a name="microsoft-domains"></a>Domini Microsoft

| Dominio| Scopo |
| ----------------------------------- |---------------------------|
| *.live.com| Gestione delle credenziali |
| app.vssps.visualstudio.com| Metadati del programma di installazione|
| vortex.data.microsoft.com | Segnalazione di arresti anomali del sistema ed errori |
| az667904.vo.msecnd.net| Segnalazione di arresti anomali del sistema ed errori |
| xamarin.com | Metadati del programma di installazione|
| xampubdl.blob.core.windows.net| Pacchetti del programma di installazione|
| download.visualstudio.microsoft.com | Pacchetti del programma di installazione|
| xamarin.azureedge.net | Pacchetti del programma di installazione|
| developer.xamarin.com | Pacchetti del programma di installazione|
| static.xamarin.com | Pacchetti del programma di installazione|
| dl.xamarin.com | Pacchetti del programma di installazione|
| dc.services.visualstudio.com| Segnalazione di arresti anomali del sistema |

### <a name="third-party-domains"></a>Domini di terze parti

| Dominio| Scopo |
| --------------------------|-------------------------|
| dl.google.com | Android SDK |
| download.oracle.com | SDK per Java|
| api.apple-cloudkit.com| Servizi di sicurezza Apple |

## <a name="use-visual-studio-for-mac"></a>Usare Visual Studio per Mac

Per assicurarsi di avere accesso a tutte le funzionalità necessarie in Visual Studio per Mac protetto da un proxy o un firewall, è consigliabile aggiungere all'elenco di elementi consentiti le porte e i domini seguenti.

### <a name="general"></a>Generale

| Dominio | Porte|Scopo|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Risoluzione degli URL Microsoft |
| vsstartpage.blob.core.windows.net| 80/443| Dati della pagina iniziale|
| software.xamarin.com |  80/443|Servizio di aggiornamento|
| addins.monodevelop.com | 80/443| Servizi di estensione |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Notifiche e funzionalità sperimentali |
| targetednotifications.azurewebsites.net|  80/443| Usato per filtrare un elenco globale delle notifiche in un elenco applicabile solo a specifici tipi di computer/scenari di utilizzo|

### <a name="identity"></a>Identità

| Dominio | Porte|Scopo|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Provider di identità|
| secure.aadcdn.microsoftonline-p.com | 80/443|Provider di identità|
| dc.services.visualstudio.com| 80/443|Segnalazione di arresti anomali del sistema|
| management.azure.com|80/443| API dei servizi di Azure |

### <a name="nuget"></a>NuGet

| Dominio | Porte|Scopo|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|API NuGet|
| secure.aadcdn.microsoftonline-p.com |80/443| Provider di identità|

### <a name="android-projects"></a>Progetti Android

| Dominio| Scopo|
| ------------------------------------|------------------------------------|
| time.android.com| Server di riferimento ora per l'emulatore Android |
| connectivitycheck.gstatic.com | Connettività per l'emulatore Android|
| cloudconfig.googleapis.com| API per l'emulatore Android|

## <a name="see-also"></a>Vedi anche

- [Installare e usare Visual Studio e i servizi di Azure protetti da un firewall o un server proxy](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Risolvere problemi simili in Windows](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
