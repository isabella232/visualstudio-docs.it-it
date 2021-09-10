---
title: Informazioni sulle configurazioni della build
description: Questo articolo descrive le varie configurazioni della build disponibili in Visual Studio per Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 0bd35d415a60ea64c479b19cb506c58c2c346cc0
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123961848"
---
# <a name="understanding-build-configurations"></a>Informazioni sulle configurazioni della build

## <a name="project-build-configurations"></a>Configurazioni della build di progetti

I progetti hanno tendenzialmente più configurazioni e passare da una configurazione a un'altra consente di ottenere output diversi in fase di compilazione. Con una configurazione di debug, ad esempio, l'output includerà simboli di debug che consentono al debugger di risolvere i nomi delle funzioni, dei parametri o delle variabili dall'analisi dello stack di un'applicazione bloccata. Anche se queste informazioni aggiuntive sono utili durante lo sviluppo, comportano dimensioni molto maggiori dei file e non sono ideale per la distribuzione.

Ogni piattaforma ha una configurazione specifica per la compilazione.

## <a name="solution-configurations"></a>Configurazioni di soluzioni

Analogamente alle configurazioni di progetti, le configurazioni di soluzioni vengono usate per creare configurazioni personalizzate per un intero progetto. Tramite la scheda **Mapping di configurazione** in **Compilazione > Configurazioni** è possibile assegnare una configurazione di destinazione per ogni elemento della soluzione, come illustrato nell'immagine seguente:

![Opzioni di Mapping di configurazione](media/projects-and-solutions-image3.png)

Per altre informazioni sulle configurazioni, vedere il video di James Montemagno su [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg).

## <a name="run-configuration"></a>Configurazione di esecuzione

Nelle versioni precedenti di Xamarin Studio era disponibile un'opzione per impostare un progetto come **progetto di avvio**, ovvero come progetto da eseguire o di cui eseguire il debug quando veniva usato il comando di esecuzione/debug globale. Il progetto di avvio era contrassegnato dal nome in grassetto nel riquadro dei progetti.

In Visual Studio per Mac, anziché impostare un progetto di avvio, è possibile impostare una _configurazione di esecuzione_. Le configurazioni di esecuzione sono disponibili in un elenco a discesa sulla barra degli strumenti accanto al selettore della configurazione della build, come illustrato di seguito:

![Elenco a discesa della configurazione di esecuzione](media/projects-and-solutions-image8.png)

Una configurazione di esecuzione è un set di opzioni di esecuzione con un nome. Per un progetto possono essere definite diverse configurazioni per scopi diversi. Le configurazioni di esecuzione sono definite a livello di progetto. Per ogni progetto eseguibile viene creata automaticamente una configurazione predefinita, anche se è possibile aggiungerne un numero illimitato. Alcuni tipi di progetto generano automaticamente altre configurazioni di esecuzione. Ad esempio, i progetti watchOS possono generare  _configurazioni glance e notification._

Le configurazioni possono essere condivise con altri sviluppatori, nel qual caso vengono archiviate nel file con estensione csproj, o mantenute in locale, nel qual caso vengono archiviate in un file con estensione user.

### <a name="android-run-configurations"></a>Configurazioni di esecuzione Android

Le configurazioni di esecuzione per i progetti Android consentono di specificare quale ricevitore di attività, servizi o trasmissioni avviare per l'esecuzione o il debug del progetto. Per poter testare i componenti in diverse condizioni di avvio, è possibile passare dati di intent aggiuntivi e impostare flag di intent.

Alle attività diverse da `MainLauncher` è necessario aggiungere `Exported=true` all'attributo Activity per il debug su un dispositivo fisico o definire filtri di intent.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Esempi di dati che possono essere inclusi nelle configurazioni di esecuzione

L'elenco seguente offre alcuni esempi di dati che possono essere inclusi nelle configurazioni di esecuzione:

* Progetto .NET normale
  * App di avvio alternativa
  * Argomenti di avvio
  * Directory di lavoro
  * Variabili di ambiente
  * Opzioni di runtime di Mono (da usare solo se in esecuzione in Mono)
* Progetto Android
  * Punto di ingresso (attività, servizio, ricevitore)
  * Argomenti e dati di intent
* Progetto iOS
  * Modalità (normale, recupero in background)
* Progetto di estensione iOS
  * App di avvio: predefinita o personalizzata
* Progetto WatchKit
  * Modalità (Glance, notifica)
  * Payload di notifica

## <a name="see-also"></a>Vedi anche

- [Informazioni sulle configurazioni della build (Visual Studio in Windows)](/visualstudio/ide/understanding-build-configurations)
