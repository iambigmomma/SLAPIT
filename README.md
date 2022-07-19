<!-- <div id="top"></div> -->
<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
<!-- [![Contributors][contributors-shield]][contributors-url] -->
<!-- [![Forks][forks-shield]][forks-url] -->
<!-- [![Stargazers][stars-shield]][stars-url] -->
<!-- [![Issues][issues-shield]][issues-url] -->
<!-- [![MIT License][license-shield]][license-url] -->
<!-- [![LinkedIn][linkedin-shield]][linkedin-url] -->



<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://saucelabs.com/resources/topics/api-testing">
    <img src="https://saucelabs.com/images/logo-saucelabs.png" alt="Logo" >
  </a>

<h3 align="center">Sauce Labs API Testing Mocking and Contract Testing Demonstration Script </h3>

  <p align="center">
    The demo scripts for anyone wants to have a taste of mocking and contract testing on Sauce Labs API Testing
    <br />
    <a href="https://docs.saucelabs.com/api-testing/mocking/"><strong>Explore more mocking server»</strong></a>
    <br />
    <br />
    <a href="https://github.com/github_username/repo_name"><strong>Explore more contract testing»</strong></a>
    ·
    <!-- <a href="https://github.com/github_username/repo_name/issues">Report Bug</a> -->
    <!-- · -->
    <!-- <a href="https://github.com/github_username/repo_name/issues">Request Feature</a> -->
  </p>
</div>

<!-- ABOUT THE PROJECT -->
<!-- ## About The Project -->

<!-- [![Product Name Screen Shot][product-screenshot]](https://example.com) -->




<!--  -->
<!-- ### Built With -->
<!--  -->
<!-- * [Next.js](https://nextjs.org/) -->
<!-- * [React.js](https://reactjs.org/) -->
<!-- * [Vue.js](https://vuejs.org/) -->
<!-- * [Angular](https://angular.io/) -->
<!-- * [Svelte](https://svelte.dev/) -->
<!-- * [Laravel](https://laravel.com) -->
<!-- * [Bootstrap](https://getbootstrap.com) -->
<!-- * [JQuery](https://jquery.com) -->
<!--  -->
<!-- <p align="right">(<a href="#top">back to top</a>)</p> -->



<!-- GETTING STARTED -->
# Getting Started




## Prerequisites

Below are what you will need before using Sauce Labs's API testing platform,
1. A Sauce Labs account ([Log in](https://accounts.saucelabs.com/am/XUI/#login/) or sign up for a [free trial license](https://saucelabs.com/sign-up))
2. An OpenAPI spec file(```myspec.yaml``` under ```specs``` folder of this repo)
3. Docker


## Environmental setup

<!-- 1. Get a free API Key at [https://example.com](https://example.com) -->
<!-- 2. Clone the repo -->
   <!-- ```sh -->
   <!-- <!-- git clone https://github.com/github_username/repo_name.git -->
   <!-- ``` -->
<!-- 3. Install NPM packages -->
   <!-- ```sh -->
   <!-- npm install -->
   <!-- ``` -->
1. Copy & paste the ```env.sh.template``` into ```env.sh```
2. Open the ```env.sh``` and setup environmental variables. We will using Sauce Labs EU datacenter for this repo.
  -  HOOK_ID: Go to the API Testing dashboard, select a project, go to webhooks and generate one. Copy just the alphanumeric ID (not the whole URL)
  -  BUILD_ID: This can be anything like 627 or 123
   ```sh
   export SPEC_FILE=demoapi.yaml
   export SAUCE_USERNAME='ENTER YOUR USERNAME'
   export SAUCE_ACCESS_KEY='ENTER YOUR ACCESSKEY'
   export HOOK_ID='ENTER YOUR HOOOK ID'
   export BUILD_ID='ENTER YOUR BUILD ID'
   export PIESTRY_PORT=6000
   export DC=api.us-central-1.saucelabs.com
   ```
3. Run ```./env.sh```
<p align="right">(<a href="#top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
# Usage

## 1. Basic
[TBD]



## 2. Mocking server

[What is piestry?]
[What is the value to use piestry?]
[How to use piestry?]


Run the following commands to start a local Piestry mocking server

```sh
docker run -v "$(pwd)/specs:/specs" -p $PIESTRY_PORT:5000 quay.io/saucelabs/piestry -u /specs/myspec.yaml
```
Note: For Apple silicon user( ex: Macbook with M1 chipset), you may encounter below message and resolve it by following this [link](https://stackoverflow.com/questions/66662820/m1-docker-preview-and-keycloak-images-platform-linux-amd64-does-not-match-th)

```sh
WARNING: The requested image's platform (linux/amd64) does not match the detected host platform (linux/arm64/v8) and no specific platform was requested
```


Execute below example commands to hit the local mocking server

```sh
#Get dynamic generated release-notes
curl localhost:$PIESTRY_PORT/api/v1/release-notes

#Get echo
curl localhost:$PIESTRY_PORT/api/v1/echo

#Get user
curl -u "example_username:1234" localhost:$PIESTRY_PORT/api/v1/user/

#Get specific user
curl -u "example_username:1234" localhost:$PIESTRY_PORT/api/v1/user/foobar

curl -u "example_username:1234" localhost:$PIESTRY_PORT/api/v1/user/dumbbar
```
![local-mocking-server-example](/assests/mocking-server.gif)



## 3. Contract testing
[What is contract testing?]

[What is the value of contract testing?]

[When should you use contract testing?]

### Usecase: Access local development environment

If your new change already deployed into an non-public facing environment(ex: ```localhost``` or staging server), you can use Sauce Connect to setup tunnel for secure access together with APIT. Please follow below steps,

1. Initiate a Sauce Connect tunnel. You can follow this [quickstart](https://docs.saucelabs.com/api-testing/sauce-connect/)
2. Once established, please click into the project page and select the tunnel under the Run All button
3. Click Run All button and API testing can test the your local backend system


### Usecase: Access production environment
TBD

## How to use Logger?


By adding the ```--logger``` and ```insights/events/_contract```together 
with your Sauce Labs API Testing 
endpoint, the logging records 
could also visible on that project dashboard
```sh
docker run -v "$(pwd)/specs:/specs" -p 6000:5000 quay.io/saucelabs/piestry -u /specs/myspec.yaml --logger https://$SAUCE_USERNAME:$SAUCE_ACCESS_KEY@$SAUCE_API_ENDPOINT/$HOOK_ID/insights/events/_contract
```
![local-contract-testing-example](/assests/contract-testing.gif)


By adding the ```--logger``` together 
with your Sauce Labs API Testing 
endpoint, the endpoint hitting records 
could also visible on the logplatform

```sh
docker run -v "$(pwd)/specs:/specs" -p 6000:5000 quay.io/saucelabs/piestry -u /specs/myspec.yaml --logger https://$SAUCE_USERNAME:$SAUCE_ACCESS_KEY@$SAUCE_API_ENDPOINT/$HOOK_ID/logger
```
![logger-example](/assests/logger.gif)

<p align="right">(<a href="#top">back to top</a>)</p>

### Test against the development environment

<!-- CONTRIBUTING -->
<!-- ## Contributing -->
<!--  -->
<!-- <!-- <!-- <!-- Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**. --> 
<!--  -->
<!-- <!-- <!-- <!-- If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement". -->
<!-- <!-- Don't forget to give the project a star! Thanks again! --> 
<!--  -->
<!-- 1. Fork the Project -->
<!-- <!-- 2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`) --> 
<!-- <!-- 3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`) --> 
<!-- <!-- 4. Push to the Branch (`git push origin feature/AmazingFeature`) --> 
<!-- 5. Open a Pull Request -->
<!--  -->
<!-- <!-- <p align="right">(<a href="#top">back to top</a>)</p> --> 



<!-- LICENSE -->
<!-- ## License -->

<!-- Distributed under the MIT License. See `LICENSE.txt` for more information. -->

<!-- <p align="right">(<a href="#top">back to top</a>)</p> -->



<!-- CONTACT -->
## Contact

Jeff Fan - jeff.fan@saucelabs.com

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
<!-- ## Acknowledgments -->
<!--  -->
<!-- * []() -->
<!-- * []() -->
<!-- * []() -->
<!--  -->
<!-- <p align="right">(<a href="#top">back to top</a>)</p> -->



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/github_username/repo_name.svg?style=for-the-badge
[contributors-url]: https://github.com/github_username/repo_name/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/github_username/repo_name.svg?style=for-the-badge
[forks-url]: https://github.com/github_username/repo_name/network/members
[stars-shield]: https://img.shields.io/github/stars/github_username/repo_name.svg?style=for-the-badge
[stars-url]: https://github.com/github_username/repo_name/stargazers
[issues-shield]: https://img.shields.io/github/issues/github_username/repo_name.svg?style=for-the-badge
[issues-url]: https://github.com/github_username/repo_name/issues
[license-shield]: https://img.shields.io/github/license/github_username/repo_name.svg?style=for-the-badge
[license-url]: https://github.com/github_username/repo_name/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/linkedin_username
[product-screenshot]: images/screenshot.png
