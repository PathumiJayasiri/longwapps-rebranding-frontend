<template>
  <div class="bg-white text-white">
    <!-- Newsletter Section -->
    <div class="newsletter q-pa-lg flex justify-between items-center rounded-corners">
      <div class="justify-center">
        <h6 class="text-white q-mb-xs">Subscribe to our newsletter</h6>
        <p class="text-grey-3">Receive latest updates and technologies to your email.</p>
      </div>
      <div class="flex items-center gap-2">
        <q-input
          v-model="email"
          type="email"
          placeholder="email"
          outlined
          dense
          input-class="text-white"
          class="newsletter-input"
        />

        <q-btn
          color="deep-purple-7"
          text-color="white"
          label="Subscribe"
          unelevated
          class="newsletter-btn"
        />
      </div>
    </div>

    <!-- Links & Company Info -->
    <div class="row link-row q-pa-xl q-col-gutter-lg">
      <!-- Column 1: Products -->
      <div class="col-6 col-md-2">
        <div class="text-subtitle1">Products</div>
        <ul class="list-none q-mt-sm">
          <li><a href="#" class="footer-link">Products 1</a></li>
          <li><a href="#" class="footer-link">Products 2</a></li>
          <li><a href="#" class="footer-link">Products 3</a></li>
        </ul>
      </div>

      <!-- Column 2: Services -->
      <div class="col-6 col-md-2">
        <div class="text-subtitle1">Services</div>
        <ul class="list-none q-mt-sm">
          <li><a href="#" class="footer-link">Services 1</a></li>
          <li><a href="#" class="footer-link">Services 2</a></li>
          <li><a href="#" class="footer-link">Services 3</a></li>
        </ul>
      </div>

      <!-- Column 3: Blogs -->
      <div class="col-6 col-md-2">
        <div class="text-subtitle1">Blogs</div>
        <ul class="list-none q-mt-sm">
          <li><a href="#" class="footer-link">Blogs 1</a></li>
          <li><a href="#" class="footer-link">Blogs 2</a></li>
          <li><a href="#" class="footer-link">Blogs 3</a></li>
        </ul>
      </div>
      <!-- Column 4: careers -->
      <div class="col-6 col-md-2">
        <div class="text-subtitle1">Careers</div>
        <ul class="list-none q-mt-sm">
          <li><a href="#" class="footer-link">Careers 1</a></li>
          <li><a href="#" class="footer-link">Careers 2</a></li>
          <li><a href="#" class="footer-link">Careers 3</a></li>
        </ul>
      </div>
      <!-- Column 5: Aboutus -->
      <div class="">
        <div class="text-subtitle1">About us</div>
        <ul class="list-none q-mt-sm">
          <li><a href="#" class="footer-link">About us 1</a></li>
          <li><a href="#" class="footer-link">About us 2</a></li>
          <li><a href="#" class="footer-link">About us 3</a></li>
        </ul>
      </div>
    </div>

    <!-- Links & Company Info -->
    <div class="row link-row q-pa-xl q-col-gutter-lg">
      <!-- Left: Company Info (1/2 width) -->
      <div class="col-12 col-md-3 company-info">
        <!-- Logo -->
        <q-img src="~assets/logo.png" alt="LONGWApps Logo" style="max-width: 200px" />
        <p class="text-body2 q-mt-sm">
          We are a US-based software company specializing in delivering innovative software
          solutions by leveraging top-tier talent and development resources in Sri Lanka.
        </p>
      </div>

      <!-- Right: Link Sets in a Row (1/2 width) -->
      <div class="col-12 col-md-6">
        <div class="row justify-between">
          <!-- Set 1 -->
          <div class="col-md-4">
            <ul class="list-none">
              <li>
                <q-btn flat round icon="email" class="q-mr-sm" />
                <a href="mailto:info@longwapps.com" class="footer-link">info@longwapps.com</a>
              </li>
              <li>
                <q-btn flat round icon="facebook" class="q-mr-sm" />
                <a class="footer-link" href="https://facebook.com/longwapps">LONGWApps (Pvt) Ltd</a>
              </li>
              <li class="flex items-center q-gutter-sm">
                <q-btn
                  flat
                  round
                  class="q-mr-sm"
                  style="font-size: 10px; color: #0077b5; padding-left: 10px"
                >
                  <!-- <q-icon class="fab fa-linkedin-in" /> -->
                  <q-img src="~assets/icons/linkedin.png" />
                </q-btn>
                <a
                  href="https://linkedin.com/company/longwapps"
                  class="footer-link"
                  target="_blank"
                  rel="noopener"
                >
                  LONGWApps (Pvt) Ltd
                </a>
              </li>
            </ul>
          </div>
          <!-- Set 2 -->
          <div class="col-md-4">
            <ul class="list-none">
              <!-- Phone -->
              <li class="flex items-center">
                <q-btn flat round icon="phone" class="q-mr-sm" />
                <a class="footer-link" href="tel:+1(970)7160978">US: +1 (970) 716 0978</a>
              </li>

              <!-- Address -->
              <li class="flex items-start q-mt-sm">
                <q-btn flat round icon="location_on" class="q-mr-sm" />
                <div>
                  <div class="flex items-center">
                    <span class="footer-link font-bold">LONGWApps LLC</span>
                  </div>
                  <div class="footer-link">
                    16192 Coastal Hwy,<br />
                    Lewes, DE 19958,<br />
                    United States
                  </div>
                </div>
              </li>
            </ul>
          </div>
          <!-- Set 3 -->
          <div class="col-md-4">
            <ul class="list-none">
              <!-- Phone -->
              <li class="flex items-center">
                <q-btn flat round icon="phone" class="q-mr-sm" />
                <a class="footer-link" href="tel:+94(77)7632068">LK: +94 (77) 763 2068</a>
              </li>

              <!-- Address -->
              <li class="flex items-start q-mt-sm">
                <q-btn flat round icon="location_on" class="q-mr-sm" />
                <div>
                  <div class="flex items-center">
                    <span class="footer-link font-bold">LONGWApps (Pvt) Ltd</span>
                  </div>
                  <div class="footer-link">
                    229/50, St.Joseph Street,<br />
                    Negombo, WP 11500,<br />
                    Sri Lanka
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>
        <!--2nd row-->
        <!-- <div class="row">
          <li>
            <q-btn flat round icon="facebook" class="q-mr-sm" />
            <a class="footer-link" href="https://facebook.com/longwapps">LONGWApps (Pvt) Ltd</a>
          </li>
          <li class="flex items-start row-address">
            <q-btn flat round icon="location_on" class="q-mr-sm" />
            <div>
              <span class="footer-link"><b>LONGWApps LLC</b></span
              ><br />
              <span class="footer-link">16192 Coastal Hwy, Lewes, DE 19958, United States</span>
            </div>
          </li>
        </div> -->
        <!--3rd row-->
        <!-- <div class="row">
          <li>
            <q-btn flat round icon="fab fa-linkedin-in" class="q-mr-sm" />
            <a class="footer-link" href="https://linkdin.com/longwapps">LONGWApps (Pvt) Ltd</a>
          </li>

          <li class="flex items-start row-address">
            <q-btn flat round icon="location_on" class="q-mr-sm" />
            <div>
              <span class="footer-link"><b>LONGWApps (Pvt) Ltd</b></span
              ><br />
              <span class="footer-link"
                >229/50, St.Joseph Street, Negombo, WP 11500, Sri Lanka</span
              >
            </div>
          </li>
        </div> -->
      </div>
    </div>
    <!-- Social Media -->
    <!-- <div class="q-pa-md flex justify-center q-gutter-md">
      <q-btn round flat icon="mdi-facebook" class="footer-icon" />
      <q-btn round flat icon="mdi-linkedin" class="footer-icon" />
    </div> -->

    <q-separator color="grey-10" spaced />

    <!-- Bottom Bar -->
    <div class="q-pa-md text-center text-grey-5 text-body2 flex justify-center items-center">
      <a href="#" class="footer-link footer-link-bottom q-mr-md">Privacy Policy</a>
      <!-- <span class="q-mx-sm">|</span> -->
      <a href="#" class="footer-link footer-link-bottom q-mr-md">Terms & Conditions</a>
      <span class="q-mx-sm copyright">|</span>
      <span class="copyright">© 2025 LONGWApps (Pvt) Ltd</span>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
const email = ref('');
</script>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'AppFooter',
});
</script>

<style scoped>
.newsletter {
  background: #36004c;
  border-radius: 8px;
  margin-left: 40px;
  margin-right: 40px;
  margin-top: 40px;
}
.newsletter-heading {
  font-family: 'Headings/Subheading/Family', sans-serif;
  font-weight: 500;
  font-style: normal;
  font-size: 20px;
  line-height: 24px;
  letter-spacing: 0;
}
.newsletter-input {
  min-width: 500px;
  background: #36004c;
  border-radius: 6px;
  color: white;
}

/* Force white border on outlined input */
.newsletter-input {
  border: 1px solid white !important;
}

/* Ensure input text is white */
.newsletter-input input {
  color: white !important;
}

/* Placeholder styling */
.newsletter-input ::placeholder {
  color: #ddd;
}
.newsletter-btn {
  border-radius: 6px;
  margin-left: 10px;
}
.link-row {
  justify-content: space-between;
}
.text-subtitle1 {
  color: #696969;
  font-weight: 500;
}
.company-links ul {
  padding: 0;
  margin: 0;
}
.company-info {
  color: #696969;
}
.company-links li {
  margin-bottom: 8px;
}

.company-links .footer-link {
  color: #b0b0b0;
  text-decoration: none;
  transition: color 0.2s;
}

.company-links .footer-link:hover {
  color: white;
}
ul {
  padding: 0;
}
li {
  margin-bottom: 8px;
  list-style: none;
  color: #696969;
}
.row-address {
  margin-left: 60px;
}
.footer-link {
  color: #696969;
  text-decoration: none;
  /* transition: color 0.2s; */
}
.footer-link:hover {
  color: #aba6a6;
}
.footer-icon {
  color: #b0b0b0;
  transition: color 0.2s;
}
.footer-icon:hover {
  color: white;
}
.footer-link-bottom {
  font-family: 'Inter', sans-serif;
}
.copyright {
  color: #696969;
}
</style>
