---
title: Informazioni sulle configurazioni della build
description: Questo articolo descrive le varie configurazioni della build disponibili in Visual Studio per Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: d1511434a34017a7f0f7da65fe1ea6956d45d497
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128408"
---
# <a name="understanding-build-configurations"></a>Informazioni sulle configurazioni della build

È possibile archiviare diverse configurazioni di proprietà della soluzione e del progetto da usare in tipi diversi di compilazioni durante il processo di sviluppo. I progetti creati da Visual Studio per Mac usando un modello includeranno in genere configurazioni di debug e di rilascio che supportano rispettivamente il debug di un'app e la distribuzione di un'app. 

Se si vuole creare configurazioni personalizzate, vedere [creazione e modifica di configurazioni di compilazione](/visualstudio/mac/create-and-edit-configurations).

>[!NOTE]
>Questo argomento si applica a Visual Studio per Mac. Per Visual Studio in Windows, vedere [informazioni sulle configurazioni di compilazione](/visualstudio/ide/understanding-build-configurations).

## <a name="solution-configurations"></a>Configurazioni di soluzioni

Le configurazioni della soluzione vengono usate per specificare le configurazioni per tutti i progetti in una soluzione. Usando la scheda **mapping di configurazione** nell'elemento **Build > Configurations** è possibile assegnare una configurazione di destinazione per ogni elemento nella soluzione aperta. Questa operazione è illustrata nell'immagine seguente:

![Opzioni di Mapping di configurazione](media/projects-and-solutions-image3.png)

Per altre informazioni sulle configurazioni, vedere il video di James Montemagno su [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg).

## <a name="project-build-configurations"></a>Configurazioni della build di progetti

I progetti tendono a avere più configurazioni. La configurazione e la piattaforma di destinazione di un progetto vengono usate insieme per specificare le proprietà da usare durante la compilazione. Il cambio tra le configurazioni consente output diversi in fase di compilazione. Con una configurazione di debug, ad esempio, l'output includerà simboli di debug che consentono al debugger di risolvere i nomi delle funzioni, dei parametri o delle variabili dall'analisi dello stack di un'applicazione bloccata. Anche se queste informazioni aggiuntive sono utili durante lo sviluppo, comportano dimensioni molto maggiori dei file e non sono ideale per la distribuzione.

Ogni piattaforma ha una configurazione specifica per la compilazione. È possibile accedere alle pagine di configurazione della compilazione per i progetti passando alla sezione **compilazione** nella finestra di dialogo **Opzioni progetto** . Aprire questa finestra di dialogo facendo clic con il pulsante destro del mouse sul progetto e scegliendo **Opzioni** o facendo doppio clic sul progetto in Esplora soluzioni.

## <a name="run-configuration"></a>Configurazione dell'esecuzione

Visual Studio per Mac consente di impostare una _configurazione di esecuzione_. Le configurazioni di esecuzione sono disponibili in un elenco a discesa sulla barra degli strumenti accanto al selettore della configurazione della build, come illustrato di seguito:

![Elenco a discesa della configurazione di esecuzione](media/projects-and-solutions-image8.png)

Una configurazione di esecuzione è un set di opzioni di esecuzione con un nome. Per un progetto possono essere definite diverse configurazioni per scopi diversi. Le configurazioni di esecuzione sono definite a livello di progetto e un valore predefinito verrà creato automaticamente per ogni progetto eseguibile, anche se è possibile aggiungere il numero desiderato. Alcuni tipi di progetto generano automaticamente altre configurazioni di esecuzione. Ad esempio, i progetti watchOS possono generare _configurazioni per Glances e notifiche_.

Le configurazioni possono essere condivise con altri sviluppatori (nel qual caso le configurazioni verranno archiviate nel file con estensione csproj) o mantenute localmente (nel qual caso verranno archiviate in un file con estensione user).

### <a name="android-run-configurations"></a>Configurazioni di esecuzione Android

Le configurazioni di esecuzione per i progetti Android consentono la specifica di un particolare attività, servizio o ricevitore di trasmissione da avviare durante l'esecuzione o il debug del progetto. È possibile passare i dati in eccesso e impostare i flag di Intent per testare i componenti in condizioni di avvio diverse.

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

## <a name="see-also"></a>Vedere anche

- [Informazioni sulle configurazioni della build (Visual Studio in Windows)](/visualstudio/ide/understanding-build-configurations)
