---
author: pkrebs
ms.author: pkrebs
title: Provisioning di una nuova soluzione di percorsi di apprendimento multilingue
ms.date: 02/10/2019
description: Eseguire il provisioning del sito Microsoft 365 Learning pathways tramite il servizio di provisioning di SharePoint
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 6948162d8a96c9a6582484c5f4fc8acad18405a7
ms.sourcegitcommit: f355885fb93d66abf61df535fa704ccdb8df9b64
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/05/2020
ms.locfileid: "45038996"
---
# <a name="provision-a-new-learning-pathways-multilingual-solution"></a><span data-ttu-id="46db6-103">Provisioning di una nuova soluzione di percorsi di apprendimento multilingue</span><span class="sxs-lookup"><span data-stu-id="46db6-103">Provision a new learning pathways multilingual solution</span></span>
<span data-ttu-id="46db6-104">Le organizzazioni che non dispongono di percorsi di apprendimento provisioning nel tenant possono utilizzare il servizio di provisioning di SharePoint per aggiungere la soluzione di percorsi di apprendimento multilingue.</span><span class="sxs-lookup"><span data-stu-id="46db6-104">Organizations that that don’t have learning pathways provisioned in their tenant can use the SharePoint Provisioning Service to add the multilingual learning pathways solution.</span></span> <span data-ttu-id="46db6-105">Con questa opzione, il modello di percorsi di apprendimento di SharePoint viene convertito in nove lingue e può essere utilizzato con una modifica minima.</span><span class="sxs-lookup"><span data-stu-id="46db6-105">With this option, the learning pathways SharePoint template is translated into nine languages and can be used with a minimum of modification.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="46db6-106">Se è già stato effettuato il provisioning dei percorsi di apprendimento nel tenant, è consigliabile seguire il [percorso di aggiornamento](custom_update_ml.md) per i percorsi di apprendimento.</span><span class="sxs-lookup"><span data-stu-id="46db6-106">If you already have learning pathways provisioned in your tenant, it's recommended that you follow the [update path](custom_update_ml.md) for learning pathways.</span></span> <span data-ttu-id="46db6-107">Se si installano percorsi di apprendimento su un'istanza esistente del tenant, le eventuali modifiche apportate al modello di sito percorsi di apprendimento o alle playlist potrebbero andare perse.</span><span class="sxs-lookup"><span data-stu-id="46db6-107">If you install learning pathways over an existing instance in your tenant, any changes made to the the learning pathways site template or playlists may be lost.</span></span>

## <a name="prerequisites-for-multilingual-support"></a><span data-ttu-id="46db6-108">Prerequisiti per il supporto multilingue</span><span class="sxs-lookup"><span data-stu-id="46db6-108">Prerequisites for multilingual support</span></span>
 
<span data-ttu-id="46db6-109">Per configurare correttamente i percorsi di apprendimento di Microsoft 365 con il servizio di provisioning, la persona che effettua il provisioning deve soddisfare i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="46db6-109">To successfully set up Microsoft 365 learning pathways with the Provisioning Service, the person doing the provisioning must meet the following pre-requisites:</span></span> 
 
- <span data-ttu-id="46db6-110">I percorsi di apprendimento per il provisioning delle persone devono essere un amministratore tenant del tenant in cui verrà eseguito il provisioning dei percorsi di apprendimento.</span><span class="sxs-lookup"><span data-stu-id="46db6-110">The person provisioning learning pathways must be a Tenant Administrator of the tenant where learning pathways will be provisioned.</span></span>  
- <span data-ttu-id="46db6-111">Un catalogo app tenant deve essere disponibile all'interno dell'opzione Apps dell'interfaccia di amministrazione di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="46db6-111">A tenant App Catalog must be available within the Apps option of the SharePoint Admin Center.</span></span> <span data-ttu-id="46db6-112">Se nell'organizzazione non è presente un catalogo delle app di SharePoint tenant, fare riferimento alla [documentazione di SharePoint Online](https://docs.microsoft.com/sharepoint/use-app-catalog) per crearne uno.</span><span class="sxs-lookup"><span data-stu-id="46db6-112">If your organization doesn't have an SharePoint tenant App Catalog, refer to the [SharePoint Online documentation](https://docs.microsoft.com/sharepoint/use-app-catalog) to create one.</span></span> <span data-ttu-id="46db6-113">Prima di eseguire il provisioning dei percorsi di apprendimento, è necessario attendere almeno due ore dopo aver creato il catalogo app.</span><span class="sxs-lookup"><span data-stu-id="46db6-113">You must wait at least two hours after creating the App Catalog before provisioning learning pathways.</span></span>  
- <span data-ttu-id="46db6-114">I percorsi di apprendimento per il provisioning delle persone devono essere proprietari di una raccolta siti del catalogo app tenant.</span><span class="sxs-lookup"><span data-stu-id="46db6-114">The person provisioning learning pathways must be a Site Collection Owner of the Tenant App Catalog.</span></span> <span data-ttu-id="46db6-115">Se il provisioning dei percorsi di apprendimento della persona non è un proprietario della raccolta siti del catalogo app, [completare queste istruzioni](addappadmin.md) e continuare.</span><span class="sxs-lookup"><span data-stu-id="46db6-115">If the person provisioning learning pathways is not a Site Collection Owner of the App Catalog, [complete these instructions](addappadmin.md) and continue.</span></span> 

## <a name="ensure-the-tenant-admin-account-doesnt-have-a-language-selected"></a><span data-ttu-id="46db6-116">Assicurarsi che l'account amministratore tenant non disponga di una lingua selezionata</span><span class="sxs-lookup"><span data-stu-id="46db6-116">Ensure the Tenant Admin account doesn't have a language selected</span></span>
<span data-ttu-id="46db6-117">Prima di eseguire il provisioning dei percorsi di apprendimento, assicurarsi che l'account di amministratore per il tenant non disponga di una lingua selezionata.</span><span class="sxs-lookup"><span data-stu-id="46db6-117">Before you provision learning pathways, ensure that the Admin Account for the tenant doesn't have a language selected.</span></span> <span data-ttu-id="46db6-118">Ecco come verificare se l'account amministratore non dispone di una lingua selezionata.</span><span class="sxs-lookup"><span data-stu-id="46db6-118">Here’s how to verify if the Admin account doesn't have a language selected.</span></span> 
1.  <span data-ttu-id="46db6-119">Con il profilo di amministratore del server perimetrale, passare a office.com.</span><span class="sxs-lookup"><span data-stu-id="46db6-119">With your Edge Admin profile, go to office.com.</span></span>
2.  <span data-ttu-id="46db6-120">Immettere le credenziali utente (se necessario).</span><span class="sxs-lookup"><span data-stu-id="46db6-120">Enter the user credentials (if necessary).</span></span>
3.  <span data-ttu-id="46db6-121">In Microsoft 365, fare clic su **tutte le app** > approfondire.</span><span class="sxs-lookup"><span data-stu-id="46db6-121">In Microsoft 365, click **All Apps** > Delve.</span></span> 
4.  <span data-ttu-id="46db6-122">Fare clic su **me**  >  **Update profile**.</span><span class="sxs-lookup"><span data-stu-id="46db6-122">Click **Me** > **Update Profile**.</span></span>
5.  <span data-ttu-id="46db6-123">Scorrere verso il basso la pagina e fare clic su **come è possibile modificare le impostazioni internazionali e della lingua**.</span><span class="sxs-lookup"><span data-stu-id="46db6-123">Scroll down the page and click **How can I change language and regional settings**.</span></span>
6.  <span data-ttu-id="46db6-124">Fare clic **qui**e quindi fare clic sui puntini di ellisse **.**</span><span class="sxs-lookup"><span data-stu-id="46db6-124">Click **here**, and then click the ellipses **...**.</span></span>
7.  <span data-ttu-id="46db6-125">In **My Display languages**, non è necessario visualizzare le **lingue selezionate**.</span><span class="sxs-lookup"><span data-stu-id="46db6-125">Under **My Display Languages**, you should see **No languages selected**.</span></span> <span data-ttu-id="46db6-126">Se è selezionata una lingua, deselezionarla.</span><span class="sxs-lookup"><span data-stu-id="46db6-126">If a language is selected, unselect it.</span></span>

### <a name="to-provision-learning-pathways"></a><span data-ttu-id="46db6-127">Per eseguire il provisioning di percorsi di apprendimento</span><span class="sxs-lookup"><span data-stu-id="46db6-127">To provision learning pathways</span></span>

1. <span data-ttu-id="46db6-128">Passare alla [pagina Microsoft 365 Learning pathways Solution](https://provisioning.sharepointpnp.com/details/3df8bd55-b872-4c9d-88e3-6b2f05344239).</span><span class="sxs-lookup"><span data-stu-id="46db6-128">Go to the [Microsoft 365 learning pathways solution page](https://provisioning.sharepointpnp.com/details/3df8bd55-b872-4c9d-88e3-6b2f05344239).</span></span>
2. <span data-ttu-id="46db6-129">Fare clic su **Aggiungi al tenant**.</span><span class="sxs-lookup"><span data-stu-id="46db6-129">Click **Add to your tenant**.</span></span> <span data-ttu-id="46db6-130">Se non è stato eseguito l'accesso al tenant, il servizio di provisioning richiederà le credenziali di amministratore tenant.</span><span class="sxs-lookup"><span data-stu-id="46db6-130">If you aren't signed into to your tenant, the Provisioning Service will ask for your Tenant Admin credentials.</span></span> 
3. <span data-ttu-id="46db6-131">Nella finestra di dialogo autorizzazioni richieste selezionare **consenso per conto dell'organizzazione** e quindi selezionare **accetta**.</span><span class="sxs-lookup"><span data-stu-id="46db6-131">From the Permissions requested dialog box, select **Consent on behalf of your organization** and then select **Accept**.</span></span>

<span data-ttu-id="46db6-132">Il servizio di provisioning richiede queste autorizzazioni per creare il catalogo app tenant, installare l'applicazione nel catalogo app tenant e provisionare il modello di sito.</span><span class="sxs-lookup"><span data-stu-id="46db6-132">The provisioning service requires these permissions to create the tenant App Catalog, install the application into the tenant App Catalog and provision the site template.</span></span> <span data-ttu-id="46db6-133">Non è previsto alcun impatto generale sul tenant.</span><span class="sxs-lookup"><span data-stu-id="46db6-133">There's no overall impact on your tenant.</span></span> <span data-ttu-id="46db6-134">Queste autorizzazioni vengono utilizzate in modo esplicito per l'installazione della soluzione.</span><span class="sxs-lookup"><span data-stu-id="46db6-134">These permissions are explicitly used for the purpose of the solution installation.</span></span> <span data-ttu-id="46db6-135">È necessario accettare queste autorizzazioni per continuare con l'installazione.</span><span class="sxs-lookup"><span data-stu-id="46db6-135">You must accept these permissions to continue with the installation.</span></span>

4. <span data-ttu-id="46db6-136">Completare i campi nella pagina informazioni di provisioning in base alle proprie esigenze per l'installazione.</span><span class="sxs-lookup"><span data-stu-id="46db6-136">Complete the fields on the provisioning information page as appropriate for your installation.</span></span> <span data-ttu-id="46db6-137">Immettere almeno l'indirizzo di posta elettronica in cui si desidera ottenere le notifiche relative al processo di provisioning e l'URL di destinazione per il sito di cui eseguire il provisioning.</span><span class="sxs-lookup"><span data-stu-id="46db6-137">At a minimum, enter the email address where you wish to get notifications about the provisioning process and the destination URL for your site to be provisioned to.</span></span>  
> [!NOTE]
> <span data-ttu-id="46db6-138">Rendere l'URL di destinazione per il sito una cosa semplice per i dipendenti, ad esempio "/sites/MyTraining" o "/teams/LearnMicrosoft365".</span><span class="sxs-lookup"><span data-stu-id="46db6-138">Make the destination URL for your site something friendly to your employees such as "/sites/MyTraining" or "/teams/LearnMicrosoft365".</span></span>

![inst_options.png](media/inst_options.png)

6. <span data-ttu-id="46db6-140">Fare clic su **provisioning** quando si è pronti per installare percorsi di apprendimento nell'ambiente tenant.</span><span class="sxs-lookup"><span data-stu-id="46db6-140">Click **Provision** when ready to install learning pathways into your tenant environment.</span></span>  <span data-ttu-id="46db6-141">Il processo di provisioning può richiedere fino a 15 minuti.</span><span class="sxs-lookup"><span data-stu-id="46db6-141">The provisioning process can take up to 15 minutes.</span></span> <span data-ttu-id="46db6-142">L'utente riceverà una notifica tramite posta elettronica quando il sito sarà pronto.</span><span class="sxs-lookup"><span data-stu-id="46db6-142">You will be notified via email when the site is ready.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="46db6-143">L'amministratore tenant che accantona il sito percorsi di apprendimento deve passare al sito e quindi aprire **CustomLearningAdmin. aspx** per inizializzare le proprietà di amministratore di percorsi di apprendimento.</span><span class="sxs-lookup"><span data-stu-id="46db6-143">The Tenant Admin who provisions the learning pathways site must go to the site, and then open **CustomLearningAdmin.aspx** to initialize learning pathways Admin properties.</span></span> <span data-ttu-id="46db6-144">A questo punto, l'amministratore del tenant deve anche assegnare i proprietari al sito.</span><span class="sxs-lookup"><span data-stu-id="46db6-144">At this time, the Tenant Admin should also assign Owners to the site.</span></span> 

## <a name="validate-provisioning-success-and-initialize-the-customconfig-list"></a><span data-ttu-id="46db6-145">Convalidare il provisioning di esito positivo e inizializzare l'elenco CustomConfig</span><span class="sxs-lookup"><span data-stu-id="46db6-145">Validate Provisioning Success and Initialize the CustomConfig List</span></span>

<span data-ttu-id="46db6-146">Al termine del provisioning, l'amministratore del tenant che ha eseguito il provisioning del sito riceve un messaggio di posta elettronica dal servizio di provisioning PnP.</span><span class="sxs-lookup"><span data-stu-id="46db6-146">When provisioning is complete, the Tenant Admin who provisioned the site receives an email from the PnP Provisioning Service.</span></span> <span data-ttu-id="46db6-147">Il messaggio di posta elettronica contiene un collegamento al sito.</span><span class="sxs-lookup"><span data-stu-id="46db6-147">The email contains a link to the site.</span></span> <span data-ttu-id="46db6-148">A questo punto, l'amministratore del tenant deve passare al sito utilizzando il collegamento fornito nel messaggio di posta elettronica e configurare il sito per il primo utilizzo:</span><span class="sxs-lookup"><span data-stu-id="46db6-148">At this point, the Tenant Admin should go to the site using the link provided in the email and set up the site for first use:</span></span>

- <span data-ttu-id="46db6-149">Passare a `<YOUR-SITE-COLLECTION-URL>sites/<YOUR-SITE-NAME>/SitePages/CustomLearningAdmin.aspx`.</span><span class="sxs-lookup"><span data-stu-id="46db6-149">Go to `<YOUR-SITE-COLLECTION-URL>sites/<YOUR-SITE-NAME>/SitePages/CustomLearningAdmin.aspx`.</span></span> <span data-ttu-id="46db6-150">L'apertura di **CustomLearningAdmin. aspx** consente di inizializzare l'elemento di elenco **CustomConfig** che consente di configurare i percorsi di apprendimento per il primo utilizzo.</span><span class="sxs-lookup"><span data-stu-id="46db6-150">Opening **CustomLearningAdmin.aspx** initializes the **CustomConfig** list item that sets up learning pathways for first use.</span></span> <span data-ttu-id="46db6-151">Dovrebbe essere visualizzata una pagina simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="46db6-151">You should see a page that looks like this:</span></span>

![cg-adminapppage.png](media/cg-adminapppage.png)

## <a name="add-owners-to-site"></a><span data-ttu-id="46db6-153">Aggiungere proprietari al sito</span><span class="sxs-lookup"><span data-stu-id="46db6-153">Add Owners to Site</span></span>
<span data-ttu-id="46db6-154">Come amministratore del tenant, è improbabile che tu sia la persona che Personalizza il sito, quindi dovrai assegnare alcuni proprietari al sito.</span><span class="sxs-lookup"><span data-stu-id="46db6-154">As the Tenant Admin, it's unlikely you'll be the person customizing the site, so you'll need to assign a few owners to the site.</span></span> <span data-ttu-id="46db6-155">I proprietari dispongono di privilegi amministrativi per il sito in modo che possano modificare le pagine del sito e rimarcare il sito.</span><span class="sxs-lookup"><span data-stu-id="46db6-155">Owners have administrative privileges on the site so they can modify site pages and rebrand the site.</span></span> <span data-ttu-id="46db6-156">Sono inoltre in grado di nascondere e visualizzare contenuto e creare playlist e sottocategorie personalizzate.</span><span class="sxs-lookup"><span data-stu-id="46db6-156">They also have the ability to hide and show content and build custom playlist and subcategories.</span></span>  

1. <span data-ttu-id="46db6-157">Scegliere **autorizzazioni sito**dal menu **Impostazioni** di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="46db6-157">From the SharePoint **Settings** menu, click **Site Permissions**.</span></span>
2. <span data-ttu-id="46db6-158">Fare clic su **Impostazioni avanzate di autorizzazione**.</span><span class="sxs-lookup"><span data-stu-id="46db6-158">Click **Advanced Permission Settings**.</span></span>
3. <span data-ttu-id="46db6-159">Fare clic su **Microsoft 365 Learning pathways owners**.</span><span class="sxs-lookup"><span data-stu-id="46db6-159">Click **Microsoft 365 learning pathways Owners**.</span></span>
4. <span data-ttu-id="46db6-160">Fare clic su **nuovo**  >  **Aggiungi utenti a questo gruppo**e quindi aggiungere le persone che si desidera siano proprietari.</span><span class="sxs-lookup"><span data-stu-id="46db6-160">Click **New** > **Add Users to this group**, and then add the people you want to be Owners.</span></span> 
5. <span data-ttu-id="46db6-161">Aggiungere un collegamento per [esplorare il sito](custom_exploresite.md) nel messaggio di condivisione e quindi fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="46db6-161">Add a link to [Explore the Site](custom_exploresite.md) in the Share message, and then click **Share**.</span></span>

## <a name="add-translators-to-the-site"></a><span data-ttu-id="46db6-162">Aggiungere i traduttori al sito</span><span class="sxs-lookup"><span data-stu-id="46db6-162">Add translators to the site</span></span>
<span data-ttu-id="46db6-163">Se si utilizzeranno i traduttori per il sito, è possibile assegnargli le autorizzazioni.</span><span class="sxs-lookup"><span data-stu-id="46db6-163">If you will be using translators for the site, you can assign them permissions.</span></span> <span data-ttu-id="46db6-164">I traduttori richiedono autorizzazioni per i membri o superiori.</span><span class="sxs-lookup"><span data-stu-id="46db6-164">Translators require Member permissions or higher.</span></span> 

## <a name="choose-options-for-using-multiple-languages-on-the-site"></a><span data-ttu-id="46db6-165">Scegliere le opzioni per l'utilizzo di più lingue nel sito</span><span class="sxs-lookup"><span data-stu-id="46db6-165">Choose options for using multiple languages on the site</span></span>
<span data-ttu-id="46db6-166">Il servizio di provisioning di SharePoint crea il sito percorsi di apprendimento in nove lingue.</span><span class="sxs-lookup"><span data-stu-id="46db6-166">The SharePoint Provisioning Service creates the Learning Pathways site in nine languages.</span></span> <span data-ttu-id="46db6-167">Vengono applicati i seguenti suggerimenti:</span><span class="sxs-lookup"><span data-stu-id="46db6-167">The following recommendations apply:</span></span>
- <span data-ttu-id="46db6-168">Disattivare le lingue che non si desidera supportare</span><span class="sxs-lookup"><span data-stu-id="46db6-168">Turn off the languages you don’t want to support</span></span>
- <span data-ttu-id="46db6-169">Se non si supporta un sito in più lingue, disattivare la funzionalità multilingue.</span><span class="sxs-lookup"><span data-stu-id="46db6-169">If you are not supporting a multilingual site, turn off the multi-lingual feature.</span></span> <span data-ttu-id="46db6-170">Vedere la sezione relativa alla disattivazione del supporto multilingue più avanti in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="46db6-170">See the "Turn off multilingual support" section later in this topic.</span></span>

### <a name="remove-languages-you-dont-want-to-support"></a><span data-ttu-id="46db6-171">Rimuovere le lingue che non si desidera supportare</span><span class="sxs-lookup"><span data-stu-id="46db6-171">Remove languages you don’t want to support</span></span>
<span data-ttu-id="46db6-172">Per le organizzazioni che scelgono di supportare una sola lingua, oltre alla lingua inglese predefinita, è consigliabile rimuovere le lingue che non sono supportate.</span><span class="sxs-lookup"><span data-stu-id="46db6-172">For organizations that choose to support only one language, in addition to the default English language, we recommend removing languages that aren’t supported.</span></span> 
1. <span data-ttu-id="46db6-173">Dal sito percorsi di apprendimento selezionare **Impostazioni** dall'alto a destra della pagina e quindi selezionare **informazioni sito**.</span><span class="sxs-lookup"><span data-stu-id="46db6-173">From the Learning Pathways site, select **Settings** from the top-right of the page, and then select **Site information**.</span></span>
2. <span data-ttu-id="46db6-174">Nella parte inferiore del riquadro delle informazioni del sito selezionare **Visualizza tutte le impostazioni del sito**.</span><span class="sxs-lookup"><span data-stu-id="46db6-174">At the bottom of the site information pane, select **View all site settings**.</span></span>
3. <span data-ttu-id="46db6-175">In **Amministrazione sito**selezionare **Impostazioni lingua**.</span><span class="sxs-lookup"><span data-stu-id="46db6-175">Under **Site Administration**, select **Language settings**.</span></span>
4. <span data-ttu-id="46db6-176">In **attiva pagine e notizie da tradurre in più lingue**, scorrere l'interruttore **su**attivato.</span><span class="sxs-lookup"><span data-stu-id="46db6-176">Under **Enable pages and news to be translated into multiple languages**, slide the toggle to **On**.</span></span> <span data-ttu-id="46db6-177">Dovrebbe essere attiva per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="46db6-177">It should be On by default.</span></span>
5. <span data-ttu-id="46db6-178">In Aggiungi o Rimuovi lingue sito fare clic su **Rimuovi** per rimuovere le lingue che non sono necessarie per il sito.</span><span class="sxs-lookup"><span data-stu-id="46db6-178">Under Add or remove site languages, click **Remove** to remove the languages you don't need for the site.</span></span> <span data-ttu-id="46db6-179">Di seguito è riportato un esempio della pagina Impostazioni lingua per mostrare l'italiano supportato per il sito, oltre alla lingua inglese predefinita.</span><span class="sxs-lookup"><span data-stu-id="46db6-179">The following shows an example of the Language Settings page to show Italian supported for the site, in addition to the default English language.</span></span>

![custom_update_ml_langsettings.png](media/custom_update_ml_langsettings.png)

> [!NOTE]
> <span data-ttu-id="46db6-181">Quando si rimuovono le lingue, non è possibile rimuovere la lingua inglese predefinita.</span><span class="sxs-lookup"><span data-stu-id="46db6-181">When removing languages you cannot remove the default English language.</span></span> 

### <a name="assign-translators"></a><span data-ttu-id="46db6-182">Assegnare i traduttori</span><span class="sxs-lookup"><span data-stu-id="46db6-182">Assign translators</span></span>
<span data-ttu-id="46db6-183">Se si intende tradurre le pagine, facoltativamente assegnare uno o più traduttori per ogni lingua (eccetto la lingua predefinita del sito).</span><span class="sxs-lookup"><span data-stu-id="46db6-183">If you're going to translate pages, optionally assign one or more translators for each language (except the site default language).</span></span> 
- <span data-ttu-id="46db6-184">Nella colonna **Translator** , iniziare a digitare il nome di una persona che si desidera essere un traduttore, quindi selezionare il nome nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="46db6-184">In the **Translator** column, start typing the name of a person you want to be a translator, and then select the name from the list.</span></span> 

> [!NOTE]
> <span data-ttu-id="46db6-185">Tutti gli utenti di Active Directory dell'organizzazione possono essere assegnati come traduttori.</span><span class="sxs-lookup"><span data-stu-id="46db6-185">Anyone in your organization's Active Directory can be assigned as a translator.</span></span> <span data-ttu-id="46db6-186">Alle persone assegnate come traduttori non verranno automaticamente concesse le autorizzazioni appropriate.</span><span class="sxs-lookup"><span data-stu-id="46db6-186">People assigned as translators will not automatically be given appropriate permissions.</span></span> <span data-ttu-id="46db6-187">Quando un utente che non dispone di autorizzazioni di modifica per un sito tenta di accedere al sito, verrà indirizzato a una pagina Web in cui è possibile richiedere l'accesso.</span><span class="sxs-lookup"><span data-stu-id="46db6-187">When someone without edit permissions to a site tries to access the site, they will be directed to a web page where they can request access.</span></span>

## <a name="turn-off-multilingual-support"></a><span data-ttu-id="46db6-188">Disattiva supporto multilingue</span><span class="sxs-lookup"><span data-stu-id="46db6-188">Turn off multilingual support</span></span>
<span data-ttu-id="46db6-189">Se non si desidera un sito multilingue, ad esempio si desidera un sito solo in lingua inglese, è consigliabile disattivare la funzionalità multilingue.</span><span class="sxs-lookup"><span data-stu-id="46db6-189">If you don’t want a multilingual site, for example, you want an English-only site, it’s recommended that you turn off the multilingual feature.</span></span> 

1. <span data-ttu-id="46db6-190">Dal sito percorsi di apprendimento selezionare **Impostazioni** dall'alto a destra della pagina e quindi selezionare **informazioni sito**.</span><span class="sxs-lookup"><span data-stu-id="46db6-190">From the Learning Pathways site, select **Settings** from the top-right of the page, and then select **Site information**.</span></span>
2. <span data-ttu-id="46db6-191">Nella parte inferiore del riquadro delle informazioni del sito selezionare **Visualizza tutte le impostazioni del sito**.</span><span class="sxs-lookup"><span data-stu-id="46db6-191">At the bottom of the site information pane, select **View all site settings**.</span></span>
3. <span data-ttu-id="46db6-192">In **Amministrazione sito**selezionare **Impostazioni lingua**.</span><span class="sxs-lookup"><span data-stu-id="46db6-192">Under **Site Administration**, select **Language settings**.</span></span>
4. <span data-ttu-id="46db6-193">In **attiva pagine e notizie da tradurre in più lingue**, scorrere l'interruttore **su**attivato.</span><span class="sxs-lookup"><span data-stu-id="46db6-193">Under **Enable pages and news to be translated into multiple languages**, slide the toggle to **On**.</span></span> <span data-ttu-id="46db6-194">Dovrebbe essere attiva per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="46db6-194">It should be On by default.</span></span>
- <span data-ttu-id="46db6-195">In **attiva pagine e notizie da tradurre**, selezionare **disattivata**.</span><span class="sxs-lookup"><span data-stu-id="46db6-195">Under **Enable pages and news to be translated**, select **Off**.</span></span> 

### <a name="add-languages"></a><span data-ttu-id="46db6-196">Aggiungere le lingue</span><span class="sxs-lookup"><span data-stu-id="46db6-196">Add languages</span></span>
<span data-ttu-id="46db6-197">I percorsi di apprendimento supportano 9 lingue, ma è consigliabile aggiungere solo le lingue necessarie per il supporto per il sito percorsi di apprendimento.</span><span class="sxs-lookup"><span data-stu-id="46db6-197">Learning pathways supports 9 languages, but it’s recommended that you add only the languages you need to support for the learning pathways site.</span></span> <span data-ttu-id="46db6-198">È possibile aggiungere lingue in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="46db6-198">You can add langauges at any time.</span></span> 
- <span data-ttu-id="46db6-199">In **Aggiungi o Rimuovi lingue sito**, iniziare a digitare un nome di lingua in **Seleziona o digitare una**lingua oppure scegliere una lingua dall'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="46db6-199">Under **Add or remove site languages**, start typing a language name in **Select or type a language**, or choose a language from the dropdown.</span></span> <span data-ttu-id="46db6-200">È possibile ripetere questo passaggio per aggiungere più lingue.</span><span class="sxs-lookup"><span data-stu-id="46db6-200">You can repeat this step to add multiple languages.</span></span> <span data-ttu-id="46db6-201">È possibile aggiungere o rimuovere le lingue dal sito in qualsiasi momento tornando alla pagina.</span><span class="sxs-lookup"><span data-stu-id="46db6-201">You can add or remove languages from your site at any time by going back to this page.</span></span>


