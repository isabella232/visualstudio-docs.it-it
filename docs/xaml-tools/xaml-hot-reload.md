---
title: Scrivere codice XAML ed eseguirne il debug Ricaricamento rapido XAML
description: Ricaricamento rapido XAML, o Modifica e continuazione XAML, consente di apportare modifiche al codice XAML durante l'esecuzione di app
ms.date: 09/23/2020
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- multiple
ms.openlocfilehash: 50fa8c216da426172a30d7b3b1adf2254dad4e28adeac9b05055de5e9bfa094b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351518"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Scrivere ed eseguire il debug del codice XAML in Ricaricamento rapido XAML in Visual Studio

Ricaricamento rapido XAML consente di compilare l'interfaccia utente dell'app WPF o UWP, consentendo di apportare modifiche al codice XAML mentre l'app è in esecuzione. Ricaricamento rapido è disponibile sia in Visual Studio che Blend per Visual Studio. Questa funzionalità consente di compilare e testare in modo incrementale il codice XAML con il vantaggio del contesto dati dell'app in esecuzione, dello stato di autenticazione e di altre complessità reali difficili da simulare durante la fase di progettazione. Per informazioni sulla risoluzione dei problemi Ricaricamento rapido XAML, vedere [Risoluzione dei Ricaricamento rapido XAML.](xaml-hot-reload-troubleshooting.md)

> [!NOTE]
> Se si usa Xamarin.Forms, vedere [Ricaricamento rapido XAML per Xamarin.Forms.](/xamarin/xamarin-forms/xaml/hot-reload)

Ricaricamento rapido XAML è particolarmente utile in questi scenari:

* Correzione dei problemi dell'interfaccia utente rilevati nel codice XAML dopo l'avvio dell'app in modalità di debug.

* Creazione di un nuovo componente dell'interfaccia utente per un'app in fase di sviluppo, sfruttando al tempo stesso il contesto di runtime dell'app.

|Tipi di applicazioni supportati|Sistema operativo e strumenti|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+ e .NET Core</br>Windows 7 e versioni successive |
|App Windows universali (UWP)|Windows 10 e successive, con Windows 10 [SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393+ |

La figura seguente illustra l'uso della struttura ad albero visuale in tempo reale per aprire il codice sorgente e quindi Ricaricamento rapido XAML modificare il testo e il colore del pulsante.

![Ricaricamento rapido XAML](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Visual Studio Ricaricamento rapido XAML è attualmente supportato solo quando si esegue l'applicazione in Visual Studio o Blend per Visual Studio con il debugger collegato (**F5** o **Avvia debug**). Non è possibile abilitare questa [](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) esperienza usando Associa a processo a meno che non si imposta [manualmente una variabile di ambiente](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process).

## <a name="known-limitations"></a>Limitazioni note

Di seguito sono riportate le limitazioni note di Ricaricamento rapido XAML. Per aggirare eventuali limitazioni, è sufficiente arrestare il debugger e quindi completare l'operazione.

|Limitazione|WPF|UWP|Note|
|-|-|-|-|
|Connessione di eventi ai controlli mentre l'app è in esecuzione|Non supportato|Non supportato|Vedere l'errore: *Verificare che l'evento non sia riuscito.* Si noti che in WPF è possibile fare riferimento a un gestore eventi esistente. Nelle app UWP non è supportato il riferimento a un gestore eventi esistente.|
|Creazione di oggetti risorsa in un dizionario risorse, ad esempio quelli nella pagina/finestra dell'app o *in App.xaml*|Supportato a partire Visual Studio 2019 Update 2|Supportato|Esempio: aggiunta di un `SolidColorBrush` oggetto in un dizionario risorse da usare come `StaticResource` .</br>Nota: le risorse statiche, i convertitori di stile e altri elementi scritti in un dizionario risorse possono essere applicati/usati durante l'uso Ricaricamento rapido XAML. Non è supportata solo la creazione della risorsa.</br> Modifica della proprietà del dizionario `Source` risorse.|
|Aggiunta di nuovi controlli, classi, finestre o altri file al progetto durante l'esecuzione dell'app|Non supportato|Non supportato|Nessuno|
|Gestione NuGet pacchetti (aggiunta/rimozione/aggiornamento di pacchetti)|Non supportato|Non supportato|Nessuno|
|Modifica data binding che usa l'estensione di markup {x:Bind}|N/A|Supportato a partire Visual Studio 2019|Questa operazione richiede Windows 10 versione 1809 (build 10.0.17763). Non supportato in Visual Studio 2017 o versioni precedenti.|
|La modifica delle direttive x:Uid non è supportata|N/D|Non supportato|Nessuno|
|Più processi | Supportato | Supportato | Supportato in Visual Studio 2019 [versione 16.6 e](/visualstudio/releases/2019/release-notes-v16.6) successive |

## <a name="error-messages"></a>messaggi di errore

Potrebbero verificarsi gli errori seguenti durante l'uso Ricaricamento rapido XAML.

|Messaggio di errore|Descrizione|
|-|-|
|Verificare che l'evento non sia riuscito|L'errore indica che si sta tentando di collegare un evento a uno dei controlli, che non è supportato durante l'esecuzione dell'applicazione.|
|Questa modifica non è supportata da Ricaricamento rapido XAML e non verrà applicata durante la sessione di debug.|L'errore indica che la modifica che si sta tentando non è supportata da Ricaricamento rapido XAML. Arrestare la sessione di debug, apportare la modifica e quindi riavviare la sessione di debug. Se si trova uno scenario non supportato che si desidera visualizzare come supportato, usare la nuova opzione "Suggerisci una funzionalità" in Visual Studio [Developer Community](https://aka.ms/feedback/suggest?space=8). |

## <a name="see-also"></a>Vedi anche

* [Risoluzione dei problemi relativi al ricaricamento rapido XAML](xaml-hot-reload-troubleshooting.md)
* [Ricaricamento rapido XAML per Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload)
* [Modifica e continuazione (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
