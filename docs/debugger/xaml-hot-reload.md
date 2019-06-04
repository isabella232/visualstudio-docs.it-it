---
title: Scrivere ed eseguire il debug di XAML tramite Ricarica hot XAML
description: Ricaricare XAML a caldo o XAML, modifica e continuazione, consente di apportare modifiche al codice XAML durante l'esecuzione delle App
ms.custom: ''
ms.date: 02/28/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f526cc8d5ff7835b3d0b942325f5755898fad147
ms.sourcegitcommit: c6249a8f3054db881ba62f4e80bf006d440f5a2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2019
ms.locfileid: "66462150"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Scrittura e debug del codice XAML in esecuzione con ricaricamento a caldo di XAML in Visual Studio

Visual Studio XAML hot ricaricare consente di compilare l'app WPF o UWP dell'interfaccia utente, consentendo di apportare modifiche al codice XAML durante l'esecuzione dell'app. Questa funzionalità consente di compilare e testare il codice XAML con il vantaggio del contesto dati dell'app in esecuzione, lo stato di autenticazione e altre complessità del mondo reale che è difficile da simulare in fase di progettazione in modo incrementale.

Ricarica hot XAML risulta particolarmente utile in questi scenari:

* Risoluzione dei problemi dell'interfaccia utente disponibili nel codice XAML dopo che l'app è stato avviato in modalità di debug.

* La creazione di un nuovo componente dell'interfaccia utente per un'app che è in fase di sviluppo, sfruttando al contesto di runtime dell'app.

|Tipi di applicazioni supportate|Sistema operativo e strumenti|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+</br>Windows 7 e versioni successive |
|App di Windows universale (UWP)|Windows 10 e versioni successive, con la [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

> [!NOTE]
> Ricarica attivo di Visual Studio XAML è attualmente supportata solo quando si esegue l'applicazione in Visual Studio con il debugger collegato (**F5** oppure **Avvia debug**). Non è possibile abilitare questa esperienza utilizzando *Connetti a processo*.

## <a name="known-limitations"></a>Limitazioni note

Di seguito sono noti limitazioni di XAML a caldo ricarica. Per risolvere qualsiasi limitazione che si verifica, solamente l'arresto del debugger e quindi completare l'operazione.

|Limitazione|WPF|UWP|Note|
|-|-|-|-|
|Collegare gli eventi ai controlli durante l'esecuzione dell'app|Non supportato|Non supportato|Errore, vedere: *Verificare l'evento non è riuscita*|
|Creazione di oggetti di risorse in un dizionario risorse, ad esempio quelli nella pagina o finestra dell'app o *App*|Non supportato|Supportato|Esempio: aggiunta di un ```SolidColorBrush``` in un dizionario risorse per l'utilizzo come un ```StaticResource```.</br>Nota: Risorse statiche, convertitori di tipi di stile e altri elementi scritti in un dizionario risorse possono essere applicato o utilizzato durante l'utilizzo di ricaricamento a caldo di XAML. Non è supportata solo la creazione della risorsa.</br> La modifica del dizionario risorse ```Source``` proprietà.| 
|Aggiunta di nuovi controlli, le classi, windows o altri file al progetto durante l'esecuzione dell'app|Non supportato|Non supportato|nessuno|
|La gestione dei pacchetti NuGet (aggiunta/rimozione/aggiornamento di pacchetti)|Non supportato|Non supportato|nessuno|
|Modifica data binding, che usa l'estensione di markup {X:Bind}|N/D|Supportato in Visual Studio 2019 e versioni successive|Non è supportato in Visual Studio 2017 o versioni precedenti|

## <a name="error-messages"></a>Messaggi di errore

È possibile imbattersi nei seguenti errori durante l'utilizzo di ricaricamento a caldo di XAML.

|Messaggio di errore|Descrizione|
|-|-|-|
|Verificare l'evento non è riuscita|Errore indica che si sta tentando di collegare un evento a uno dei controlli, che non è supportato durante l'esecuzione dell'applicazione.|
|La funzionalità Modifica e continuazione di XAML non ha trovato elementi da aggiornare.|Errore si verifica quando si sta modificando XAML che a caldo ricaricare non è possibile aggiornare nell'app.</br> Questo errore può essere talvolta risolto usando l'app in esecuzione per passare a una vista in cui viene usato il XAML.</br> In alcuni casi, questo errore indica che la modifica specifica non può essere applicata finché non si riavvia la sessione di debug. |
|Questa modifica non è supportata durante una sessione di debug.|Errore indica che la modifica desiderata non è supportata dal ricaricamento a caldo di XAML. Arrestare la sessione di debug, apportare la modifica e quindi riavviare la sessione di debug.|
