---
title: Scrivere ed eseguire il debug di XAML usando XAML Hot ReloadWrite and debug XAML using XAML Hot Reload
description: XAML Hot Reload, o modifica e continuazione XAML, consente di apportare modifiche al codice XAML durante l'esecuzione di app
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 120ae30b3a33a04f17bd2ec23b747ac41c9427cf
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880093"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Scrivere ed eseguire il debug del codice XAML in esecuzione con XAML Hot Reload in Visual StudioWrite and debug running XAML code with XAML Hot Reload in Visual Studio

XAML Hot Reload ti aiuta a compilare l'interfaccia utente dell'app WPF o UWP consentendoti di apportare modifiche al codice XAML mentre l'app è in esecuzione. Hot Reload è disponibile sia in Visual Studio che in Blend per Visual Studio. Questa funzionalità consente di compilare e testare in modo incrementale il codice XAML con il vantaggio del contesto dati dell'app in esecuzione, dello stato di autenticazione e di altre complessità reali difficili da simulare in fase di progettazione. Per informazioni sulla risoluzione dei problemi di XAML Hot Reload, vedi Risoluzione dei problemi relativi a [XAML Hot Reload.](xaml-hot-reload-troubleshooting.md)

> [!NOTE]
> Se si utilizza Xamarin.Forms, vedere [Ricarica iniziale XAML per Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload).

XAML Hot Reload è particolarmente utile in questi scenari:XAML Hot Reload is especially helpful in these scenarios:

* Risoluzione dei problemi dell'interfaccia utente rilevati nel codice XAML dopo l'avvio dell'app in modalità di debug.

* Compilazione di un nuovo componente dell'interfaccia utente per un'app in fase di sviluppo, sfruttando al contempo il contesto di runtime dell'app.

|Tipi di applicazioni supportati|Sistema operativo e strumenti|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 e .NET Core</br>Windows 7 e versioni successive |
|App Windows universali (UWP)|Windows 10 e versioni successive, con [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 |

Nella figura seguente viene illustrato l'utilizzo della struttura ad albero visuale attiva per aprire il codice sorgente e quindi XAML Hot Reload per modificare il testo del pulsante e il colore del pulsante.

![Ricaricamento rapido XAML](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Visual Studio XAML Hot Reload è attualmente supportato solo quando si esegue l'applicazione in Visual Studio o Blend per Visual Studio con il debugger collegato (**F5** o **Avvia debug**). Non è possibile abilitare questa esperienza utilizzando [Connetti per elaborare](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) a meno che non si [imposti manualmente una variabile](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process)di ambiente .

## <a name="known-limitations"></a>Limitazioni note

Di seguito sono riportate le limitazioni note di XAML Hot Reload. Per aggirare qualsiasi limitazione che si esegue in, basta arrestare il debugger e quindi completare l'operazione.

|Limitazione|WPF|UWP|Note|
|-|-|-|-|
|Eventi di cablaggio ai controlli durante l'esecuzione dell'app|Non supportato|Non supportate|Vedere error: *Ensure Event Failed*. Si noti che in WPFWPF è possibile fare riferimento a un gestore eventi esistente. Nelle app UWP non è supportato il riferimento a un gestore eventi esistente.|
|Creazione di oggetti risorsa in un dizionario risorse, ad esempio quelli nella pagina/finestra dell'app o *app.xaml*|Supportato a partire da Visual Studio 2019 Update 2Supported starting in Visual Studio 2019 Update 2|Supportato|Esempio: aggiunta `SolidColorBrush` di un in un `StaticResource`dizionario risorse da utilizzare come file .</br>Nota: le risorse statiche, i convertitori di stili e altri elementi scritti in un dizionario risorse possono essere applicati/utilizzati durante l'uso di XAML Hot Reload. Solo la creazione della risorsa non è supportata.</br> Modifica della `Source` proprietà del dizionario risorse.|
|Aggiunta di nuovi controlli, classi, finestre o altri file al progetto mentre l'app è in esecuzione|Non supportato|Non supportato|nessuno|
|Gestione dei pacchetti NuGet (aggiunta/rimozione/aggiornamento di pacchetti)|Non supportato|Non supportato|nessuno|
|Modifica dell'associazione dati che utilizza l'estensione di markup x:Bind|N/D|Supportato a partire da Visual Studio 2019Supported starting in Visual Studio 2019|Questa operazione richiede Windows 10 versione 1809 (build 10.0.17763). Non supportato in Visual Studio 2017 o versioni precedenti.|
|La modifica delle direttive x:Uid non è supportata|N/D|Non supportato|nessuno|
|Processi multipli | Non supportato | Non supportato | Il ricaricamento a caldo può essere utilizzato solo su un processo alla volta. |

## <a name="error-messages"></a>messaggi di errore

È possibile riscontrare i seguenti errori durante l'utilizzo di XAML Hot Reload.

|Messaggio di errore|Descrizione|
|-|-|
|Verifica che l'evento non sia riuscitoEnsure Event Failed|L'errore indica che si sta tentando di collegare un evento a uno dei controlli, che non è supportato durante l'esecuzione dell'applicazione.|
|Questa modifica non è supportata da XAML Hot Reload e non verrà applicata durante la sessione di debug.|L'errore indica che la modifica che si sta tentando non è supportata da XAML Hot Reload. Interrompere la sessione di debug, apportare la modifica e quindi riavviare la sessione di debug. Se si rileva uno scenario non supportato che si desidera visualizzare supportato, utilizzare la nuova opzione "Suggerisci una funzionalità" nella [community di sviluppatori](https://developercommunity.visualstudio.com/spaces/8/index.html)di Visual Studio . |

## <a name="see-also"></a>Vedere anche

* [Risoluzione dei problemi relativi al ricaricamento rapido XAML](xaml-hot-reload-troubleshooting.md)
* [Ricarica a caldo XAML per Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload)
* [Modifica e continuazione (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
