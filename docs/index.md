# Understanding India

The content and newsletter initiative for macro and nuanced understanding of socio political aspects of India.

<hr/>

<!-- =========================================================================================== -->

<h3>Sign Up for Weekly News Letter</h3>

<div id="SubPage_failed" style="display: none;">
    <h4>
        Request Failed! Try Again.
    </h4>
</div>

<form id="SubPage_SubForm" action="" onsubmit="submitEmail();return false;">
    <div class="form-group">
        <label for="emailInputField">Email address</label>
        <input
        id="emailInputField" type="email"
        onchange="validateForm()"
        onkeyup="validateForm()"
        onkeydown="validateForm()"
        onpaste="validateForm()"
        oninput="validateForm()"
        class="form-control" aria-describedby="emailHelp" placeholder="Enter email" />
    </div>
    <button id="submitButton" class="btn btn-primary" disabled=true>Submit</button>
</form>

<div id="SubPage_SubSuccessful" style="display: none;">
    <h4>
        Thank you for Subscribing.
    </h4>
</div>

<div id="SubPage_processing" style="display: none;">
    <h4>
        Processing Request...
    </h4>
</div>

<!-- =========================================================================================== -->

<br/>
<i class="fas fa-globe-asia fa-lg"></i>
<i class="fas fa-rupee-sign fa-lg"></i>
<i class="fab fa-github-alt fa-lg"></i>
<i class="fas fa-code fa-lg"></i>

[^1]: Last Updated: `2018-11-03`

<!-- =========================================================================================== -->

<script>

function validateForm() {
    var emailField =  $("#emailInputField")[0].value
    var isEmailValid = emailField.match(/^([\w.%+-]+)@([\w-]+\.)+([\w]{2,})$/i)

    if (isEmailValid == null) {
        document.getElementById("submitButton").disabled=true
        return false
    }

    document.getElementById("submitButton").disabled=false
    return true
}

function submitEmail() {
    isValidForm = validateForm()
    if (!isValidForm) {
        return
    }

    var emailField =  document.getElementById("emailInputField").value

    // TODO
    var url = ""

    document.getElementById("SubPage_SubForm").style.display = "none"
    document.getElementById("SubPage_failed").style.display = "none"
    document.getElementById("SubPage_SubSuccessful").style.display = "none"
    document.getElementById("SubPage_processing").style.display = "block"

    fetch(url, {
        method: "POST",
        headers: {
            "Accept": "application/json",
            "Content-Type": "application/json"
        },
        body: JSON.stringify({
            email: emailField
        })
    })
    .then(handleResponse)
    .then(handleSuccess)
    .catch(handleErrors)
}

function handleResponse(response) {
    if (!response.ok) {
        throw Error(response.statusText)
    }
    return response
}

function handleSuccess(response) {
    document.getElementById("SubPage_failed").style.display = "none"
    document.getElementById("SubPage_processing").style.display = "none"
    document.getElementById("SubPage_SubForm").style.display = "none"
    document.getElementById("SubPage_SubSuccessful").style.display = "block"
}

function handleErrors(error) {
    document.getElementById("SubPage_SubSuccessful").style.display = "none"
    document.getElementById("SubPage_processing").style.display = "none"
    document.getElementById("SubPage_failed").style.display = "block"
    document.getElementById("SubPage_SubForm").style.display = "block"
}

</script>
