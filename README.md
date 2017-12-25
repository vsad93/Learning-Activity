from apiclient.discovery import build
from bs4 import BeautifulSoup
from keys import developerKey

class Activity:

    def __init__(self, fileId, developerKey,sequence=False, order=0):
        #change this to oauth later? ask for developer key at init
        self.drive_service = build('drive', 'v3', developerKey=developerKey)
        html = self.get_html(fileId)
        self.soup = BeautifulSoup(html, 'html.parser')
        if sequence != False:
            self.sequence = sequence
            self.order = order #if there is no order number can I safely just add it to the beginning?

    def get_html(self, fileId):
        files = self.drive_service.files()
        response = files.export(fileId=fileId,mimeType='text/html')
        html = response.execute()
        return html

    def title(self):
        title = "not parsing"
        return title

    def subject(self):
        subject = "not parsing"
        return subject

    def concepts_practices(self):
        concepts_practices = "not parsing"
        return concepts_practices

    def project_description(self):
        project_description = "not parsing"
        return project_description

    def pacing(self):
        pacing = "not parsing"
        return pacing

    def learning_targets(self):
        return "not parsing"

    def mini_lesson(self):
        return "not parsing"

    def independent_work(self):
        return "not parsing"

    def group_work(self):
        return "not parsing"

    def exit_slip(self):
        return "not parsing"

    def rubric_checklist(self):
        return "not parsing"


activity = Activity("1J2n_XgsojFU2GuwHv8UUQvniKVO74r8fyke0RAU38jk", developerKey)
print activity.soup.prettify()
