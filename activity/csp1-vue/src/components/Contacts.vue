<script setup>
  import {ref} from "vue";

  import axios from "axios";

  import {Notyf} from "notyf";
  import 'notyf/notyf.min.css';

  const notyf = new Notyf();

  const WEB3FORM_ACCESS_KEY = "9ecbb1ed-6b38-46d1-9eb1-911997942210";

  const emailSubject = "New message from Portfolio Contact Form";

  const name = ref("");
  const email = ref("");
  const subject = ref("");
  const message = ref("");

  const isLoading = ref(false);

  const sendForms = async (e) => {
    e.preventDefault();
    isLoading.value = true;

    try {
      const response = await axios.post("https://api.web3forms.com/submit", {
        access_key: WEB3FORM_ACCESS_KEY,
        name: name.value,
        email: email.value,
        subject: subject.value || emailSubject,
        message: message.value,
      },{
        headers: {
          'Content-Type': "application/json",
          Accept: "application/json",
        },
      });

      if (response.data.success) {
        notyf.success("Message sent successfully!");
        name.value = "";
        email.value = "";
        subject.value = "";
        message.value = "";
      } else {
        notyf.error("Failed to send message. Please try again.");
      }
    } catch (error) {
      notyf.error("Something went wrong. Please try again later.");
    } finally {
      isLoading.value = false;
    }
  };

  //

</script>

<template>
  <div id="contact" class="section-light">
    <div class="container">
      <div class="text-center mb-5">
        <span class="section-tag">Get In Touch</span>
        <h2 class="section-title">Start a <span class="gradient-text">Conversation</span></h2>
        <p class="section-sub">Have a project in mind or want to collaborate? Send me a message.</p>
      </div>
      <div class="row g-4">
        <div class="col-lg-7">
          <div class="form-card">
            <form @submit.prevent="sendForms" action="#contact" method="post">
              <div class="row">
                <h5 class="contact-info-title">Contact Me</h5>
                <div class="col-md-6 mb-3">
                  <label for="name" class="form-label">Full Name</label>
                  <input v-model="name" type="text" class="form-control" id="name" name="name" placeholder="Aaron Crisologo" required />
                </div>
                <div class="col-md-6 mb-3">
                  <label for="email" class="form-label">Email Address</label>
                  <input v-model="email" type="email" class="form-control" id="email" name="email" placeholder="email@example.com" required />
                </div>
              </div>
              <div class="mb-3">
                <label for="subject" class="form-label">Subject</label>
                <input v-model="subject" type="text" class="form-control" id="subject" name="subject" placeholder="Project inquiry" />
              </div>
              <div class="mb-3">
                <label for="message" class="form-label">Project Details / Message</label>
                <textarea v-model="message" class="form-control" id="message" name="message" rows="5" placeholder="Tell me about your project..." required></textarea>
              </div>
              <button type="submit" class="btn btn-primary-custom w-100" :disabled="isLoading">{{ isLoading ? "Sending..." : "Send Message" }}</button>
            </form>
          </div>
        </div>
        <div class="col-lg-5">
          <div class="contact-info-card">
            <h5 class="contact-info-title">Contact Information</h5>

            <div class="contact-info-item">
              <span class="contact-info-icon icon-email"><i class="bi bi-envelope-fill"></i></span>
              <div class="contact-info-body">
                <span class="contact-info-label">Direct Email</span>
                <span class="contact-info-value">aaronangelodcrisologo@gmail.com</span>
              </div>
            </div>

            <div class="contact-info-item">
              <span class="contact-info-icon icon-location"><i class="bi bi-geo-alt-fill"></i></span>
              <div class="contact-info-body">
                <span class="contact-info-label">Primary Base</span>
                <span class="contact-info-value">Makati, Philippines</span>
              </div>
            </div>

            <div class="contact-info-item">
              <span class="contact-info-icon icon-role"><i class="bi bi-briefcase-fill"></i></span>
              <div class="contact-info-body">
                <span class="contact-info-label">Role</span>
                <span class="contact-info-value">Full Stack Web Developer</span>
              </div>
            </div>

            <hr class="contact-divider" />
            <p class="text-muted mb-2">Connect with me:</p>
            <div class="d-flex gap-3 social-icons">
              <a href="https://github.com/AaronCrisologo" target="_blank" rel="noopener" aria-label="GitHub" title="GitHub"><i class="bi bi-github"></i></a>
              <a href="https://www.linkedin.com/in/aaron-angelo-crisologo-4a1b97364/" target="_blank" rel="noopener" aria-label="LinkedIn" title="LinkedIn"><i class="bi bi-linkedin"></i></a>
              <a href="#landing" aria-label="Portfolio" title="Portfolio"><i class="bi bi-globe"></i></a>
            </div>

            <div class="qr-card">
              <div class="qr-code">
                <img src="https://placehold.co/120x120?text=QR" alt="Contact QR placeholder" class="img-fluid rounded" />
              </div>
              <div class="qr-body">
                <h6 class="qr-title">Instant Contact Sync</h6>
                <p class="qr-text">Scan camera directly to download mobile contact profile, portfolio &amp; credentials.</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
