// Enable all buttons, links, and input fields
document.querySelectorAll("button, a, input").forEach(el => el.removeAttribute("disabled"));

// Make hidden or locked elements visible without breaking layout
document.querySelectorAll("[style*='display: none'], [style*='visibility: hidden']").forEach(el => {
  if (el.tagName !== "BODY" && el.tagName !== "HTML") {
    el.style.display = "block"; // Show the element without affecting the page structure
  }
});

// Enable right-click functionality
document.oncontextmenu = null;
document.body.oncontextmenu = () => true;

// Remove iframe restrictions
document.querySelectorAll("iframe").forEach(el => el.remove());

// Attempt to make the Next button clickable
let nextButton = document.querySelector("[aria-label='Next'], .next-button-class");
if (nextButton) {
  nextButton.removeAttribute("disabled");
  nextButton.style.pointerEvents = "auto"; // Ensure the button is clickable
}

// Try to bypass the SCORM API and mark the course as complete
function completeSCORM() {
  try {
    // Set SCORM status to 'completed'
    if (window.API && window.API.LMSSetValue) {
      API.LMSSetValue("cmi.core.lesson_status", "completed");
      API.LMSCommit(""); // Commit changes

      // Optionally, you can also call LMSFinish() if the platform allows it
      // API.LMSFinish("");
    }
  } catch (error) {
    console.error("Error marking SCORM as complete:", error);
  }
}

// Call completeSCORM after enabling elements or performing actions
completeSCORM();
