# Adapted from https://github.com/ruby-grape/danger/blob/master/Dangerfile
# Q: What is a Dangerfile, anyway? A: See http://danger.systems/

# ------------------------------------------------------------------------------
# What changed?
# ------------------------------------------------------------------------------
has_lib_changes = !git.modified_files.grep(/^lib/).empty?
has_test_changes = !git.modified_files.grep(/^(features|spec|test)/).empty?

# ------------------------------------------------------------------------------
# You've made changes to lib, but didn't write any tests?
# ------------------------------------------------------------------------------
if has_lib_changes && !has_test_changes
  if %w(features spec test).any? { |dir| Dir.exist?(dir) }
    warn("There are code changes, but no corresponding tests. "\
         "Please include tests if this PR introduces any modifications in "\
         "behavior.",
         :sticky => false)
  else
    markdown <<-MARKDOWN
Thanks for the PR! This project lacks automated tests, which makes reviewing and approving PRs somewhat difficult. Please make sure that your contribution has not broken backwards compatibility or introduced any risky changes.

MARKDOWN
  end
end
