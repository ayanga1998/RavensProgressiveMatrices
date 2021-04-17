# RavensProgressiveMatrices

Note: Code is an adaptation of the GEN&TEST2 code created by Neha Sharma, Sumesh Vijayan, Yash Shah at Stevens Institute of Technology
    
    The notebook listed in this repository was used to create a cognitive agent capable of solving Raven's Prgoressive Matrix problems in textual form. The text data used along with the correpsonding code is included in the repository.
    
RavensProblem: 
        The class solves 2x1 Raven's Progressive Matrix Problems in textual form. It utilizes a Frame knowledge 
    representation model to process and store the data for a given problem. It then leverages Means-End Analysis 
    along with the Generate & Test method to analyze and select the most logical solution.
    
ATTRIBUTES:
  - prob: List of textual data containing the information for a given problem
  - figures: (dict) Main frame used to store the object, shape, and attribute information for each figure
       
METHODS:
  - solve(self): 
        Develops a semantic network that encapsulates the environment of the problem set.
        Uses regular expressions to match, clean and fill each state with the correct attributes and
        updates the appropriate slot in the figures frame
  - permute_fig_shapes(self, figure): 
        permutes and stores the results from figures stored in "self.figures()"
        and appends/returns the information in the dictionary "results"
  - build_transform(self, f1, f2): 
        Takes an input of two figures (either A and B or C and the remaining options) and calculates the 
        transformation that occurs between corresponding objects in each figure. Returns a dict
        of all the recorded transformations
   - identity_trans(self, shapes1, shapes2):
        Takes an input of a shape from figure 1 and figure 2 and records the transformations by detecting
        key words in each object's state that correspond to a change in attribute or position
   - build_permuted_transforms(self, fig1, fig2): 
        Uses the build_transform and permute_fig_shapes methods to store permuted transforms and 
        its attributes into a new frame
   - weight_transform_graph(self, graphs)::
        Calculates weights that influences the selection of a solution by accumulating points based on the
        presence of certain keywords
   - compare_transforms(self, t1, t2):
        Compares the goal state with a search state by calculating a difference metric that is heavily influenced
        by matching word occurrences and other factors in both states
   - generate(self):
        Generates the target/goal transformation state along with all possible search states. Returns two variables:
        target_transforms, and  choice_transforms
   - test(self, target_transforms, choice_transforms):
        Takes an input of target and candidate solutions, calculates an initial weight and score, and filters out poor solutions.
        After filtering, the all remaining states are analyzed and the one with the best score and/or weight will be selected for
        be chosen as the answer. In the event of a tie, a random decimal between 0 and 1 is generated. If the
        decimal rounds up to 1, then the current state becomes the selected solution. After all solutions are 
            tested, the method outputs the choice corresponding to the answer chosen.
