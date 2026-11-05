# Adapt this template to your Ruby framework and deployment model.
# Pin the Ruby version to the version supported by your application.
FROM ruby:3.4-slim-bookworm

ENV BUNDLE_PATH=/usr/local/bundle \
    BUNDLE_WITHOUT="development:test"

RUN apt-get update \
    && apt-get install -y --no-install-recommends ca-certificates \
    && rm -rf /var/lib/apt/lists/*

RUN groupadd --system app \
    && useradd --system --gid app --create-home --home-dir /app app

WORKDIR /app

# Copy dependency manifests first to improve build cache reuse.
COPY Gemfile Gemfile.lock ./
RUN bundle install

# Copy application source with runtime ownership.
COPY --chown=app:app . .

# Create only paths that the application needs to write.
RUN mkdir -p /app/tmp /app/log \
    && chown app:app /app/tmp /app/log

USER app

# Replace the port and command with those required by your application.
EXPOSE 3000
CMD ["bundle", "exec", "ruby", "app.rb"]
