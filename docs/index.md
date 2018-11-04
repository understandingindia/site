# <img src="img/favicon.ico" alt="Smiley face" align="middle"> Understanding India

The content and newsletter initiative for macro and nuanced understanding of socio political aspects of India.

<!-- =========================================================================================== -->

<hr/>

## Sign Up for Weekly News Letter

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

<hr/>
:arrows_clockwise: **Read: [This Week's Latest](this_week)**

<!-- =========================================================================================== -->

<hr/>
## Initiative

- To provide critical content that caters to the understanding of India, its Geo-Political, Social,
Economic and Demographic change & impact at a macro level with nuance.

- To elevate from stories with a narrow perspective and see where the bigger changes fit in for a
country that is going through transformation at a pace like never before, We need better content
to reach more people and build better prespectives.

- More often than not the trending/popular stories divert the attention and understanding from
changes happening that are slowly and steadily transforming the economy and society. We intend
to cater that content and build a more informed perspective.

<!-- =========================================================================================== -->

<hr/>
## Collaboration & Crowd-Sourcing

- We need more people to collaborate on and curate stories for the next week to incorporate
more opinions, diverse point of views and further better understanding.

- :star2: Repository: [understandingindia/collaborate](https://github.com/understandingindia/collaborate)
- [Details on Contribution & Collaboration](next_week/#collaborate-and-contribute)
- [Content Guidelines](next_week/#content-guidelines)
- [Contribute via a Pull Request](next_week/#pull-request-guide)

<!-- =========================================================================================== -->

<hr/>
## More

- :in: [This Week](this_week)

- :fast_forward: [Contribute to Next Week](next_week)

<!-- #ToDo #WeeklyReleaseUpdate To be updated, every weekly release: point to latest archive page -->
- :rewind: [Archive](archive/2018/october/oct22_oct28/)

- :star2: Repository: [understandingindia/collaborate](https://github.com/understandingindia/collaborate)

- :mailbox: Contact - email: undindia@gmail.com

<!-- =========================================================================================== -->

<hr/>

<i class="fas fa-globe-asia fa-lg"></i>
<i class="fas fa-rupee-sign fa-lg"></i>
<i class="fab fa-github-alt fa-lg"></i>
<i class="fas fa-code fa-lg"></i>

<!-- =========================================================================================== -->

[^*]: Last Updated: `2018/11`

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

    var url = "https://rp-dbasvc.appspot.com/add-email-undindia"

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
